Смоделируем работу нашего обучающего центра. У нашего центра есть преподаватели, группы и студенты. Мы пока не изучали базы данных, поэтому данные будем хранить прямо в коде.
Все что находится до 530-ой строки, трогать не нужно. Всю работу нужно проделать ниже 530-ой строки.

Что необходимо сделать?
Как мы уже сказали, в нашем центре есть преподаватели, группы и студенты. Значит для начала нам нужны структуры для этих сущностей.
Создайте 3 структуры, со следующими полями:

Person
    ID - уникальный идентификатор, положительный целочисленный тип
    Name - имя человека, строковой тип
    Surname - фамилия человека, строковой тип
    Phone - номер телефона, строковой тип

Student
    Person - встроенная структура Person, анонимное поле
    GroupID - идентификатор группы, в котором учится студент, положительный целочисленный тип
    Grades - баллы по неделям, пары ключ-значение, ключи - строковой тип, значения - целочисленный тип
    TopicsToWorkOn - список тем, в которых у студента трудности, слайс строк

Group
    ID - уникальный идентификатор, положительный целочисленный тип
    Title - название группы, строковой тип
    Tutor - преподаватель группы, объект типа Person
    Students - список студентов группы, слайс объектов Student

Нам нужна еще одна структура, чтобы сымитировать базу данных. Поля в этой структуре будут представлять таблицы настоящей БД.
Создайте структуру DB со следующими полями:

DB
    tutors - слайс объектов Person
    groups - слайс объектов Group
    students - слайс объектов Student

Вся работа этого задания будет проводиться над структурой DB. Нужно реализовать 9 методов для данной структуры, по 3 на каждую нашу сущность.
Для преподавателей:
    1. GetTutors() - возвращает список всех преподавателей центра (тип []Person)
    2. GetTutor(id uint) - возвращает одного преподавателя, или пустой объект Person
    3. SearchTutor(query string) - возвращает одного преподавателя, или пустой объект Person
Для групп:
    4. GetGroups() - возвращает список всех групп центра (тип []Group)
    5. GetGroup(id uint) - возвращает одну группу, или пустой объект Group
    6. SearchGroup(query string) - возвращает одну группу, или пустой объект Group
Для студентов:
    7. GetStudents() - возвращает список всех студентов центра (тип []Student)
    8. GetStudent(id uint) - возвращает одного студента, или пустой объект Student
    9. SearchStudent(query string) - возвращает одного студента, или пустой объект Student

Детальный разбор методов:
    Методы 1, 4, 7 (GetTutors, GetGroups, GetStudents) не имеют сложной логики и просто возвращают соответствующие поля структуры DB.
    Методы 2, 5, 8 (GetTutor, GetGroup, GetStudent) принимают один положительный, целочисленный параметр. Эти методы проходят циклом по соответствующим полям структуры DB и сравнивают ID каждого элемента с тем, который был передан в них. При нахождении соответствия, методы возвращают эти объекты (Person, Group и Student соответственно). В случае не нахождения, возвращают пустые объекты соответствующих типов.
    Методы 3, 6, 9 (SearchTutor, SearchGroup, SearchStudent) принимают один строковой параметр. Эти методы проходят циклом по соответствующим полям структуры DB и сравнивают Name, Surname, Phone в случае с SearchTutor и SearchStudent, и Title в случае с SearchGroup с переданной строкой.
    SearchTutor -> ищет по Name, Surname, Phone
    SearchGroup -> ищет по Title
    SearchStudent -> ищет по Name, Surname, Phone

Реализуйте все указанные методы, и только. Проверять можно запустив программу и вводив команды от 0 до 9. Функция main и тестовые данные уже подготовлены.