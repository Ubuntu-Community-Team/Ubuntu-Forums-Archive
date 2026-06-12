---
title: "adding strings side to side"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by quartaela on 2011-04-06
hi there i have work about listing database with a script file. there are 4 applications which are "add,delete,search, and view all contacts". and i have a simple problem when i use redirection to add name surname etc. with one by one i can't managed to adding them side by side. here is the code.

"
#!/bin/sh


echo "welcame to peop"
echo "please you select the menu"
echo " (a) Add contact, (d) Delete contact, (s) Search contact, (v) View all contact, (q) Quit"

read select

touch peop.txt

if [ $select = "a" ] 
then
echo "please enter the name"
read name 
$name >> peop.txt 
echo "please enter the surname"
read surname
$surname >> peop.txt 

echo "please enter the birth date"
read birtdate
$birtdate" >> peop.txt 

echo "please enter the phone"
read phone
$phone >> peop.txt 

echo "please enter the e-mail"
read e-mail
$e-mail >> peop.txt 

elif [ $select = "d" ]
then 

echo "please enter the name"
read name 
echo "please enter the surname"
read surname
sed '1,/^$name/d' peop.txt
sed '1,/^$surname/d' peop.txt




elif [ $select = "s" ]
then 

echo "please enter the name"
read name
grep $name peop.txt


elif [ $select = "v" ]
then
cat peop.txt

elif [ $select = "q" ]
then
echo " the program is finished !!!"

else
echo " WRONG character" 
fi 
"

---

### Post by quartaela on 2011-04-06
well friends i am waiting your answers please help :).

---

