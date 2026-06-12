---
title: "atoi function in c and number at the end of a string"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by ixchel on 2010-05-29
Hi

I am trying to read a number from a string using atoi function in c.

This is my function:

int get_number(char *stringname)
{
    int name = atoi(stringname);
    return name;
}

If stringnumber is  for example 123abc the function woks fine and returns 123.
However if the stringname is abc123 it returns 0.  

Is there anyway to get the number from such a string (abc123) with atoi
or any similar  function?
I really don't want to check for each digit in a string weather it is a number or a character.

Thanks for help.

---

### Post by Locke_99GS on 2010-05-29
You'll want to remove non-digits from the variable, or move the digits into a new variable to work with.

---

