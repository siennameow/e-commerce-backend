# E-Commerce Backend

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/siennameow/e-commerce-backend/blob/main/LICENSE)

## Description 📝 

This app is the backend portion of an E-Commerce website. Express.js was used for the server and MySQL for the database along with Sequelize as the ORM to run SQL models and queries. The SQL database includes tables for products, categories, tags, and product tags. RESTful API routes are used to make requests and updates from the database which are joined through Sequelize queries.

Link to the demo video : https://drive.google.com/file/d/1NtALINbQzl6zTXeYqq6RDM8v1E9ehbef/view

## Table of Contents 📖

* [Application Preview ⭐](#application-preview-)
* [Features 📋](#features-)
* [Code Snippet 💻](#code-snippet-)
* [Installation 🗳](#installation-)
* [Usage 💡](#usage-)
* [Technologies 🔧](#technologies-)
* [Contribution 👩🏻‍💻](#contribution-)
* [Questions ❓](#questions-)
* [Credits 🙌](#credits-)

## Application Preview ⭐

GIF demo for GET all and GET by id for categories, products and tags.
<img src="/assets/images/GET-demo.gif">

Functionality Example of Product route:

GET all products.
<img src="/assets/images/GET-ALL.png">

POST/Create product.(Add new product"Gucci bag")
<img src="/assets/images/POST-NEW.png">

GET product by ID.(Find "gucci bag" by it's id "6")
<img src="/assets/images/GET-BY-ID.png">

PUT/Update product by ID.( Price drop from 5000 usd to 4000 usd and stock changed from 5 to 3)
<img src="/assets/images/PUT-UPDATE.png">

GET product by ID after update.(Notice the price and stock are changed)
<img src="/assets/images/PUT-AFTER.png">

DELETE product by ID.
<img src="/assets/images/DELETE-BY-ID.png">

GET product after delete not found.
<img src="/assets/images/DELETE-AFTER.png">

## Features 📋

⚡️ `dotenv` to load environment variables from a .env file into `process.env` and store configuration in the environment separate from code \
⚡️ `mysql2` module to connect to MySQL database and perform queries\
⚡️ `express.js`and `sequelize` to build api routes GET (Select All), GET by id (Select by ID), POST (Create), PUT (Update), DELETE (Destroy)

## Code Snippet 💻

The GET `/api/categories/:id` route find one category by its `id` value 

```JavaScript
router.get('/:id', (req, res) => {
  Category.findOne({
    where: {
      id: req.params.id,
    },
    include: [{model: Product}],
  })
  .then (categoryData => {
    if (! categoryData) {
      res.status(404).json({ message: 'No Category found with this id'});
      return;
    }
    res.json(categoryData)
  })
  .catch (err => {
    res.status(500).json(err);
  });
});
```

The PUT `/api/categories/:id` route update a category by its `id` value
```JavaScript
router.put('/:id', (req, res) => {
  Category.update({
    category_name: req.body.category_name,
  },
  {
    where: {
      id: req.params.id,
    }
  })
  .then (categoryData => {
    if (!categoryData) {
      res.status(404).json({massage: 'No Category found with this id'});
      return;
    }
    res.json(categoryData);
  })
  .catch (err => {
    res.status(500).json(err);
  }); 
});
```
## Installation 🗳 

- Download or clone repository to use this application on local machine.
- Node.js and MySQL is required to run the application
- To install necessary dependencies, navigate to the root directory and run the following command:
>    `npm i`

## Usage 💡

For more information - Please visit the following videos on how the application works.
https://drive.google.com/file/d/1NtALINbQzl6zTXeYqq6RDM8v1E9ehbef/view

This application is running under mysql as a local host, you can modify the .env file with your own user/password to start the application.

After installation :
- Creat, Sync and Seed data: 
    - run `mysql -u root -p` in terminal and use password to login to your mysql shell
    - `source db/schema.sql` in mysql shell
    - `npm run seed` in terminal
- Functionality:
    - `npm start`in terminal to start the server
    - use [Insomnia](https://insomnia.rest/download) to view data through different routes.

## Technologies 🔧

* [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
* [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
* [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
* [Express.js](https://expressjs.com/)
* [Node.js](https://nodejs.org/en/)
* [MySQL](https://www.mysql.com/)
* [dotenv](https://www.npmjs.com/package/dotenv)
* [Sequelize](https://sequelize.org/)


## License 📜
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/siennameow/e-commerce-backend/blob/main/LICENSE)
MIT License

Copyright (c) 2022 Sienna Li

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Contribution 👩🏻‍💻 
If you would like to contribute to this project reach out to me. Contact Information can be found below or by clicking on the `Questions` link provided in the Table of Contents.

## Questions ❓

📩 If you have any question, email me here at : lihexuan1@gmail.com<br/>
:octocat: My Github page is [siennameow](https://github.com/siennameow)


## Credits 🙌

Thanks to the following people who helped me in this project:
- Jerome Chenette
- Manuel Nunes
- Vince Lee
