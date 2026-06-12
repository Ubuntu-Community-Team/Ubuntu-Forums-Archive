---
title: "Root"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Souptik on 2011-02-05
Hi, I have to run an application as root always in order to make it function properly. The app is there in the menu but without root access. Can anyone do something so that I can always run it as root ( and without the command line !!! :lolflag:) ?????

---

### Post by NightwishFan on 2011-02-05
Edit the menu in System -> Preferences -> Menu (or similar), find the menu object you want, and add "gksudo" to the front.

---

### Post by Souptik on 2011-02-05
> **NightwishFan said:**
> Edit the menu in System -> Preferences -> Menu (or similar), find the menu object you want, and add "gksudo" to the front.
thanks..... thread solved !!!!

---

### Post by jdmcclung on 2011-02-05
If you right click on the menu you should get an option to Edit menu. If not, look for Main Menu in your menu this is the program to edit the menu. Once the program open on the left is a menu that will reflect your menu. On the right is the list of programs in the selected folder of the menu. Once you find the program you want you need to do the following.

1. Click the item to select it.
2. click properties. 
3. In command line add gksudo before what is already there. 
4. Click ok then close the Menu Editor. 

Now when you run the program you should get a dialog box asking for your password.

---

### Post by Souptik on 2011-02-07
> **jdmcclung said:**
> If you right click on the menu you should get an option to Edit menu. If not, look for Main Menu in your menu this is the program to edit the menu. Once the program open on the left is a menu that will reflect your menu. On the right is the list of programs in the selected folder of the menu. Once you find the program you want you need to do the following.

1. Click the item to select it.
2. click properties. 
3. In command line add gksudo before what is already there. 
4. Click ok then close the Menu Editor. 

Now when you run the program you should get a dialog box asking for your password.
Thanks for the response

---

