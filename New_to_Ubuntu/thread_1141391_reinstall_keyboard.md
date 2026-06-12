---
title: "reinstall keyboard"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-04-28
I have found out what that my(¨) looks as shown and i have to hold shift and press the key twice for the mark to display so i copied and pasted the (") from the help form to get my alias to work right. I think I might need to reinstall my keyboard does any one know how to do that I need a gui and for more info I using a acer aspire 4720z labtop.

---

### Post by Praxicoide on 2009-04-28
You can reconfigure Xorg, which also handles your keyboard

sudo dpkg-reconfigure xserver-xorg 

It will ask you to either autodectect your keyboard, or if you want to select it manually.

---

### Post by lance bermudez on 2009-04-30
This command is not working for me. I was looking for the one that I have used before to install other keyboards like when you first install Linux the one that has you type keys on the keyboard and ask you question about keys that you may have. Does any body know what that command is. I have tried sudo dpkg-reconfigure xserver-xorg and had it auto detect my keyborad and the other opion that let me tray to select it but it is in text and gives me no choces like the install one that I was talking about.

---

