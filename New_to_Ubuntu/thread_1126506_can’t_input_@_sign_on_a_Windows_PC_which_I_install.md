---
title: "can’t input @ sign on a Windows PC which I installed Portable Ubuntu on."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by bobconnors on 2009-04-15
I have a Windows PC which I installed Portable Ubuntu -- which gives you linux on it. I’m trying to do
Python manage.py syncdb. Trouble is in Linux I’m not able to input @ sign

1	Tried  ascii representation of @ sign #64 and 
2	Tried hex representation of @ sign 40

I also tried 3 things that Googling suggested:

switched keyboard layout to "be" and keyboard model "pc105" 
ran « sudo dpkg-reconfigure -phigh xserver-xorg » and receive message that :
xserver-xorg is not installed
4	tried switching to finnish keyboard


5	tried sudo apt-get install scim-bridge

All 5 failed. Just want to be able to input @ sign.

---

### Post by llamabr on 2009-04-15
What kind of keyboard do you have?  What do you get when you hold down shift and press 2?

instead of be, try changing keyboard to en, and see what you get.

---

### Post by bobconnors on 2009-04-16
I have an HP Model # KU-0316. When I hold shift and press 2 I get
a ", which is the character over the comma on keyboard. on my keyboard shift and press 2 should be @.

i went into /etc/X11 and vi xorg.conf and switched the be to en for XkbLayout, logged out and logged in, but no change.

By the way to get to /etc/X11 the / is done by typing Shift 7.

---

### Post by bobconnors on 2009-04-17
maybe i'm coming at this the wrong way. i have python, django, and pinax installed on Ubuntu. i execute :

pubuntu@pubuntu:~/django-trunk/django/bin/mysite$ python manage.py syncdb
Creating table auth_message
Creating table auth_group
Creating table auth_user
Creating table auth_permission
Creating table django_content_type
Creating table django_session
Creating table django_site

You just installed Django's auth system, which means you don't have any superuse
rs defined.
Would you like to create one now? (yes/no):

Username (Leave blank to use 'pubuntu'):
E-mail address: bob.connors"wdc.usda.gov
Error: That e-mail address is invalid.
E-mail address:

i can't enter e-mail address because I can't enter a @ in ubuntu. 

i want to use both django and pinax. is there anyway i can do that without entering my e-mail address in python manage.py syncdb?

---

### Post by bobconnors on 2009-04-27
ubuntu 8.04 hardy heron inabilty to type @

i've been given much advice, but i have never had to deal with a situation such as this. here's the @, but when i'm in ubuntu it is gone. for me a - is / in ubuntu.

i've hunted down most keys except for the @ and when you are using django it asks for an e-mail which needs an @

---

### Post by phuckyou on 2010-07-25
With my previous post in consideration (which you can't read because the admins removed it... let's pretend you are familiar with its contents anyway), the solution to this problem is to run the command:

  dpkg-reconfigure console-setup


...and ensure the keyboard layout is "USA" (it seems to default to "Latin America").

---

