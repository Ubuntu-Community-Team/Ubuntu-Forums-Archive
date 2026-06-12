---
title: "problem with a simple if condition_?"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by quartaela on 2011-04-07
hi there i have work with construct a database about people. there is a menu which you decide what you want to do. but i have problem about this menu and redirection.

"
#!/bin/sh
#

echo "Welcome to peop"
echo "Press a for ADD a contact"
echo "Press d for DELETE a contact"
echo "Press s for SEARCH a conatact"
echo "Press v for PRINT the list"
echo "Press q for QUIT"

touch peop.txt

read menu

if [ $menu="a" ]
then
echo "Please enter the name"
read name
echo "Please enter the surname"
read surname
echo "Please enter the birthdate"
read birth
echo "Please enter the phone number"
read gsm
echo "Please enter the e-mail"
read email

$name:$surname:$birth:$gsm:$email >> peop.txt

fi
" 

the first question is why i can't print the line with this code "
$name:$surname:$birth:$gsm:$email >> peop.txt" _?

and i realize that when i press any key it enters to the if condition_?. but i want if you only press a it can enter to the if cond. i can't managed it. please help . and thanks for your help anyway. : )

---

### Post by Azdour on 2011-04-07
Hi,

If I understand correctly does the following fix your issue?:

```

echo $name:$surname:$birth:$gsm:$email >> peop.txt

```

---

### Post by quartaela on 2011-04-07
> **Azdour said:**
> Hi,

If I understand correctly does the following fix your issue?:

```

echo $name:$surname:$birth:$gsm:$email >> peop.txt

```

yess finally :). i thougt that echo is a function that prints on screen what you enter like a printf function in C. on the other hand, how can i fix the if condition statement. it always enters in _?

---

### Post by nothingspecial on 2011-04-07
And don't forget to quote your variables
echo "$name":"$surname":"$birth":"$gsm":"$email" >> peop.txt

---

### Post by quartaela on 2011-04-07
> **nothingspecial said:**
> And don't forget to quote your variables
echo "$name":"$surname":"$birth":"$gsm":"$email" >> peop.txt

this works too. so what is the diffrecence between putting quotes and not putting. cause it works in two ways_?

---

### Post by smurphy_it on 2011-04-07
without the double quotes, it won't be taken as a "literal full string".  

If you answer one of your questions, and add in a "space", it will mess you up (if you don't have the variables in a double-quote).


Try answering one of your "add" records, and put a space in the "name" or "surname" prompts, you'll see what I mean.

---

### Post by quartaela on 2011-04-07
> **smurphy_it said:**
> without the double quotes, it won't be taken as a "literal full string".  

If you answer one of your questions, and add in a "space", it will mess you up (if you don't have the variables in a double-quote).


Try answering one of your "add" records, and put a space in the "name" or "surname" prompts, you'll see what I mean.
  now i understand :). can u help about "if [ $menu="a" ]" this code. at my lab. assistant's tutorial i can't found clear information about checking char equality for menu : ). and thanks for your help anyway.

---

