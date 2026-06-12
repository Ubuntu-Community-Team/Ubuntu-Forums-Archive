---
title: "A newbie is about to explode(c++)"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by echo.whoami on 2008-12-02
I know this isn't a subject for ubuntu forums but I'm about to explode ](*,)
. I'm trying to find a solution but nothing. pls help

this is the code. What should i put into the $$$$. I know is char something but WHAT...

```

#include<iostream>
#include<string>
using namespace std;

class employee
{
  private:
    char name[20];
    char id[5];
  public:
    employee($$$$$,$$$$$); //constructor
};

void main()
{
  employee em1($$$$$$,$$$$$$); //constructor
  .
  .
  .
}

employee::employee($$$$$$,$$$$$$$)
{
  strcpy(name,$$$$$$);
  strcpy(id,$$$$$$$);
}


```

If you are really quit you'll be able to hear me (boom!!!)

---

### Post by dummyhead3 on 2008-12-02
What do you want to accomplish with this program?

---

### Post by echo.whoami on 2008-12-02
Just to pass from the main, em1("name","id"), the name and the id in the class em1. But how? 

Use the overload constructor to pass the values.

---

### Post by Zorael on 2008-12-02
(There's a full subforum named Development & Programming, by the way. Whine whine nag!)

---

### Post by kernelhaxor on 2008-12-02
Here's the Programming talk forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

You have better chances of getting help there.

---

### Post by dmizer on 2008-12-02
Closed this. Duplicate here: [http://ubuntuforums.org/showthread.php?p=6296918#post6296918](http://ubuntuforums.org/showthread.php?p=6296918#post6296918)

Please do not create duplicate threads. Use the report post button and we can move it for you.

Thank you.

---

