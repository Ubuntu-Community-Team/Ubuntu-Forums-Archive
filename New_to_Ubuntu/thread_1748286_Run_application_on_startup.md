---
title: "Run application on startup"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by thexnightmare on 2011-05-03
Dear,
How to make an applicaiton run @ startup?
Like calculator, or custom developed software.
Thx

---

### Post by edm1 on 2011-05-03
Go to system settings (in the session menu at the top right corner on 11.04) and open 'Startup Applications', click add, give it a name like "Calculator", then put the package name of the application you would like to launch in the command box. You can usually find the package name if you launch the app then go to Help>About. eg. to launch the calculator type "gcalctool" in the box.

---

### Post by tanmayiit on 2011-05-03
For application which require authentication is there anything like auto-authorize because its really annoying to type in password to start the application every time you start you computer.

---

### Post by thexnightmare on 2011-05-03
Thx edm1, solved

---

### Post by fdrake on 2011-05-03
i can actually create a small bash script and set to be run at start up, but i wouldn't suggest you to type in a file you password just like that. what kind of applications do you need to start?

---

### Post by thexnightmare on 2011-05-07
solved  by adding it from startup application, and give it root aaccess from sudo visudo to prevent asking of password

---

