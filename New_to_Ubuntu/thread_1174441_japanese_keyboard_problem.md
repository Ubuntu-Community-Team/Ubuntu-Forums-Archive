---
title: "japanese keyboard problem:"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by smalleye86 on 2009-05-30
hi guys,
i have a problem with my japanese keyboard in ubuntu 9.04 .i cant type the "}"  (i was logging on through windows now) , if i try to type the "}" it is displayed as "|"-the OR sign . i even tried to change the keyboard layout settig but it doesnt help..
thanks in advance for any kind of help.

---

### Post by freeman2000 on 2009-05-31
Try these links to Japanese/English Linux groups....

  [http://www.linux.or.jp/](http://www.linux.or.jp/) 

  [http://tlug.linux.or.jp/](http://tlug.linux.or.jp/) 

Good luck.

---

### Post by smalleye86 on 2009-06-06
i tried the website..but there wasn't the related information :(

---

### Post by smalleye86 on 2009-06-10
i figured it out!! 
the problem was, i had selected the "english" layout during the installation, so no matter what layout i chose in the system->preferences->keyboard layout, the base layout was still english..(at least this is how i view the problem)..so i used one of the sudo commands to change the layout installed during installation of ubuntu..and it worked instantly!!

just type 
sudo dpkg-reconfigure console-setup
in the command terminal, then choose your language and follow the guidelines..

cheers!!

---

