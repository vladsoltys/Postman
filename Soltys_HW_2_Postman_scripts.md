# HW_2 Postman


**1)**
---
> 1. // Отправить запрос. 
http://162.55.220.72:5005/first

> 2. // Статус код 200
```
pm.test ( "Status code is 200" , function () {
    pm.response.to.have.status(200);
});
```
> 3. // Проверить, что в body приходит правильный string.
```
pm.test ("Checkout string", function () {
    pm.expect(pm.response.text()).to.include
    ("This is the first responce from server!");
});
```
**2)** 
---

> // 1. Отправить запрос
http://162.55.220.72:5005/user_info_3

> // 2. Статус код 200
```
pm.test("Status code 200", function () {
    pm.response.to.have.status(200);
});
```
> // 3. Спарсить response body в json.
```
let JsonData = pm.response.json();
// console.log(JsonData);
```
```
let JsonAge = parseInt(JsonData.age);
let JsonName = JsonData.name
let JsonSalary = JsonData.salary
```

> // 4. Проверить, что name в ответе равно name s request (name вбить руками.)

```
pm.test("Checkout name", function () {
    pm.expect(JsonName).to.eql("Potap");
});
```

> // 5. Проверить, что age в ответе равно age s request (age вбить руками.)

```
pm.test("Checkout age", function() {
    pm.expect(JsonAge).to.eql(31);
});
```

> // 6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)

```
pm.test("Checkout salary", function () {
    pm.expect(JsonSalary).to.eql(800000);
})
```

> // 7. Спарсить request.

```
var JsonDataRequest = request.data;
//  console.log(JsonDataRequest);
```

> // 8. Проверить, что name в ответе равно name s request (name забрать из request.)

```
pm.test("Request name = response name", function () {
    pm.expect(JsonName).to.eql(JsonDataRequest.name);
});
```

> // 9. Проверить, что age в ответе равно age s request (age забрать из request.)

```
pm.test("Request age = response age", function () {
    pm.expect(JsonAge).to.eql(parseInt(JsonDataRequest.age));
});
```

> // 10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)

```
pm.test("Request salary = response salary", function () {
    pm.expect(JsonSalary).to.eql(parseInt(JsonDataRequest.salary));
});
```

> // 11. Вывести в консоль параметр family из response.

```
let JsonFamily = JsonData.family;
console.log(JsonFamily);
```

> // 12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)

```
let u_salary_1_5_year = JsonFamily.u_salary_1_5_year;
// console.log(u_salary_1_5_year);
pm.test("u_salary_1_5_year from response = salary*4", function (){
    pm.expect(u_salary_1_5_year).to.eql(parseInt(JsonDataRequest.salary)*4);
});
```

**3)**
---

> // 1. Отправить запрос.
http://162.55.220.72:5005/object_info_3

> // 2. Статус код 200
```
pm.test("Status code 200", function() {
    pm.response.to.have.status(200);
});
```

> // 3. Спарсить response body в json.
```
let responseJson = pm.response.json();
// console.log(responseJson);
```

> // 4. Спарсить request.
```
let requestJson = pm.request.url.query.toObject();
// console.log(requestJson);
```
> // 5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("request name = response name", function () {
    pm.expect(responseJson.name).to.eql(requestJson.name);
});
```
> // 6. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("request age = response age", function () {
    pm.expect(parseInt(responseJson.age)).to.eql(parseInt(requestJson.age));
});
```
> // 7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
pm.test("request salary = response salary", function () {
    pm.expect(responseJson.salary).to.eql(parseInt(requestJson.salary));
});
```
> // 8. Вывести в консоль параметр family из response.
```
let JsonFamily = responseJson.family;
console.log(JsonFamily);
```
> // 9. Проверить, что у параметра dog есть параметры name.
```
pm.test ("Checking dog include name", function () {
    pm.expect(JsonFamily.pets.dog.name).not.eql(undefined);
});
```
> // 10. Проверить, что у параметра dog есть параметры age.
```
pm.test ("Checking dog include age", function () {
    pm.expect(JsonFamily.pets.dog.age).not.eql(undefined);
});
```
> // 11. Проверить, что параметр name имеет значение Luky.
```
pm.test ("Checking dog equal Luky", function () {
    pm.expect(JsonFamily.pets.dog.name).to.eql("Luky");
});
```
> // 12. Проверить, что параметр age имеет значение 4.
```
pm.test ("Checking dog equal Luky", function () {
    pm.expect(JsonFamily.pets.dog.age).to.eql(4);
});
```

**4)**
---

> // 1. Отправить запрос.
http://162.55.220.72:5005/object_info_4

> // 2. Статус код 200
```
pm.test("Status code 200", function () {
    pm.response.to.have.status(200);
});
```

> // 3. Спарсить response body в json.
```
let responseJson = pm.response.json();
```

> // 4. Спарсить request.
```
let requestJson = pm.request.url.query.toObject();
// console.log(requestJson);
```

> // 5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("request name = response name", function () {
    pm.expect(responseJson.name).to.eql(requestJson.name);
});
```
> // 6. Проверить, что age в ответе равно age из request (age забрать из request.)
```
pm.test("request age = response age", function () {
    pm.expect(responseJson.age).to.eql(parseInt(requestJson.age));
});
```
> // 7. Вывести в консоль параметр salary из request.
```
let requestJsonSalary = requestJson.salary;
console.log(requestJsonSalary);
```
> // 8. Вывести в консоль параметр salary из response.
```
let responseJsonSalary = responseJson.salary;
console.log(responseJsonSalary);
```
> // 9. Вывести в консоль 0-й элемент параметра salary из response.
```
let responseJsonSalaryFirst = responseJson.salary[0];
console.log(responseJsonSalaryFirst);
```
> // 10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```
let responseJsonSalarySecond = responseJson.salary[1];
console.log(responseJsonSalarySecond);
```
> // 11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```
let responseJsonSalaryThird = responseJson.salary[2];
console.log(responseJsonSalaryThird);
```

> // 12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```
pm.test("request salary = response first salary", function () {
    pm.expect(responseJsonSalaryFirst).to.eql(parseInt(requestJson.salary));
});
```
> // 13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```
pm.test("request salary*2 = response second salary", function () {
    pm.expect(parseInt(responseJsonSalarySecond)).to.eql(parseInt(requestJson.salary)*2);
});
```
> // 14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```
pm.test("request salary*3 = response third salary", function () {
    pm.expect(parseInt(responseJsonSalaryThird)).to.eql(parseInt(requestJson.salary)*3);
});
```
> // 15. Создать в окружении переменную name
```
// Environments -> creating "PostmanScriptsHM" enviroment -> creating variable "name"
```
> // 16. Создать в окружении переменную age
```
// creating variable "age"
```
> // 17. Создать в окружении переменную salary
```
// creating variable "salary"
```
> // 18. Передать в окружение переменную name
```
pm.environment.set("name", requestJson.name);
```
> // 19. Передать в окружение переменную age
```
pm.environment.set("age", requestJson.age);
```
> // 20. Передать в окружение переменную salary
```
pm.environment.set("salary", requestJson.salary);
```
> // 21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```
for (let i = 0; i < responseJsonSalary.length; i++) {
  console.log(responseJsonSalary[i]);
};
```

**5)**
---

http://162.55.220.72:5005/user_info_2
> // 1. Вставить параметр salary из окружения в request
```
// salary = {{salary}}
```

> // 2. Вставить параметр age из окружения в age
```
// age = {{age}}
```

> // 3. Вставить параметр name из окружения в name
```
// name = {{name}}
```

> // 4. Отправить запрос.
```
// send
```

> // 5. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
> // 6. Спарсить response body в json.
```
let responseJson = pm.response.json();
// console.log(responseJson);
// let keys = Object.keys(responseJson);
// console.log(keys);
```

> // 7. Спарсить request.
```
let requestJson = request.data;
// console.log(requestJson);
```

> // 8. Проверить, что json response имеет параметр start_qa_salary
```
pm.test("json response include start_qa_salary", function () {
    pm.expect(Object.keys(responseJson)).to.include("start_qa_salary");
});
```
> // 9. Проверить, что json response имеет параметр qa_salary_after_6_months
```
pm.test("json response include qa_salary_after_6_months", function () {
    pm.expect(Object.keys(responseJson)).to.include("qa_salary_after_6_months");
});
```
> // 10. Проверить, что json response имеет параметр qa_salary_after_12_months
```
pm.test("json response include qa_salary_after_12_months", function () {
    pm.expect(Object.keys(responseJson)).to.include("qa_salary_after_12_months");
});
```
> // 11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```
pm.test("json response include qa_salary_after_1.5_year", function () {
    pm.expect(Object.keys(responseJson)).to.include("qa_salary_after_1.5_year");
});
```
> // 12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```
pm.test("json response include qa_salary_after_3.5_years", function () {
    pm.expect(Object.keys(responseJson)).to.include("qa_salary_after_3.5_years");
});
```
> // 13. Проверить, что json response имеет параметр person
```
pm.test("json response include person", function () {
    pm.expect(Object.keys(responseJson)).to.include("person");
});
```
> // 14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```
pm.test("start_qa_salary = request salary", function () {
    pm.expect(responseJson.start_qa_salary).to.eql(parseInt(requestJson.salary));
});
```
> // 15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```
pm.test("qa_salary_after_6_months = request salary*2", function () {
    pm.expect(responseJson.qa_salary_after_6_months).to.eql(parseInt(requestJson.salary)*2);
});
```
> // 16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```
pm.test("qa_salary_after_12_months = request salary*2.7", function () {
    pm.expect(responseJson.qa_salary_after_12_months).to.eql(parseInt(requestJson.salary)*2.7);
});
```
> // 17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```
pm.test("qa_salary_after_1.5_year = request salary*3.3", function () {
    pm.expect(responseJson["qa_salary_after_1.5_year"]).to.eql(parseInt(requestJson.salary)*3.3);
});
```

> // 18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```
pm.test("qa_salary_after_3.5_year = request salary*3.8", function () {
    pm.expect(responseJson["qa_salary_after_3.5_years"]).to.eql(parseInt(requestJson.salary)*3.8);
});
```
> // 19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```
pm.test("u_name[1] = request salary", function () {
    pm.expect(responseJson.person.u_name[1]).to.eql(parseInt(requestJson.salary));
});
```

> // 20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```
pm.test("u_age = request age", function () {
    pm.expect(responseJson.person.u_age).to.eql(parseInt(requestJson.age));
});
```
> // 21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```
pm.test("u_salary_5_years = request salary*4.2", function () {
    pm.expect(responseJson.person.u_age).to.eql(parseInt(requestJson.age));
});
```
> // 22. Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```
let person = Object.keys(responseJson.person);
// console.log(person);
for(let i = 0; i < person.length; i++){
    console.log(person[i]);
};
```
