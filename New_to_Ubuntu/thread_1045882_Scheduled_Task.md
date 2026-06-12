---
title: "Scheduled Task"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by jotremba on 2009-01-20
I had just downloaded the scheduled task program from add/remove programs and I got to wondering if there was a way to make it so some kind of message came up tomorrow morning for my wife... I could see a lot of good non utility ways that this program could be fun if it were to be able to do stuff like that.

Also it would be a great way for me to learn how to use the program.

If anyone could let me know how to do this it would be awesome....

Thanks

---

### Post by roquefilipe on 2009-01-21
This is a two step process. First you need a way to pop up a notification. I use zenity. To try that out, open up a terminal and type```
zenity --info --text="Hi, It's me. It is just a test"
``` 

This will pop up a information box with a OK button. You can mess with zenity's options to get what better fits your needs. 

Now, the second step is to scheduled it. Since you have installed Gnome Schedule you can use that. It is very intuitive, so will not explain it. Just be sure that the command is the same as in the previous step.

---

