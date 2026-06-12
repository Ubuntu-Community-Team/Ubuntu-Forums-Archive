---
title: "mv command to move all pictures from desktop"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by ollie13239 on 2009-03-10
hello =)
pretty new to the forum so sorry if this is in the wrong place .
im not complelty new to linux  but im no expert and after working on this problem i cant seem to find a solution. 

ill explain what im doing it might help 
ok so i have built as a project a digital picture frame running the latest ubunutu i no they could have been other slimmer choices of os but i like ubunutu so i chose it. 

all is fine with the exception  off the following 
when i send a file via bluetooth it goes to the desktop i cant seem to change the file path  so i came up with the idea of using the mv command to automatically move all picture files from the desktop to the my pictures folder . so here is my question 
how would  i use that command to move all pictures on the desktop to the picture folder??

 i will then  have that command run every time the 'picture frame ' is turned on .

---

### Post by taurus on 2009-03-10
What is the file extension of your images on your desktop (~/Desktop)?  If they are .jpg, you could do something like

```
mv ~/Desktop/*.jpg ~/Pictures
```

---

### Post by ollie13239 on 2009-03-10
i will try this 
thank you very much

---

### Post by ollie13239 on 2009-03-10
ok i made a mistake  and over simplified 
 could anyone explain how i would make the above command run at start up ? thanks again

---

### Post by unutbu on 2009-03-10
Click System>Pref>Sessions, click Add, and put ```
mv ~/Desktop/*.jpg ~/Pictures
``` in the text field for the command.

Or, you could edit your ~/.profile and add the command there.

---

### Post by ollie13239 on 2009-03-10
> **unutbu said:**
> Click System>Pref>Sessions, click Add, and put ```
mv ~/Desktop/*.jpg ~/Pictures
``` in the text field for the command.

Or, you could edit your ~/.profile and add the command there.


I tried the above it didnt work but i shall try the below thanks for a speedy reply

---

