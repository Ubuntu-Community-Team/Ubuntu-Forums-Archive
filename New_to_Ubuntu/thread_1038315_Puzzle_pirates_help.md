---
title: "Puzzle pirates help"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by ltcyco on 2009-01-12
Hey guys i need help i know this topic has already been posted but its like from 2 years ago and i didnt want to grave dig so yeah:
Puzzle pirates is a game and when you try to download it it tells you to put this code in the terminal:```
$ sh yohoho-install.bin
```
and i did but i got this message back:```
tony@tony:~$ sh yohoho-install.bin
sh: Can't open yohoho-install.bin
tony@tony:~$ 

```
Help please?

---

### Post by kestrel1 on 2009-01-12
You may need to sudo that:
```
sudo sh yohoho-install.bin
```

---

### Post by ltcyco on 2009-01-12
> **kestrel1 said:**
> You may need to sudo that:
```
sudo sh yohoho-install.bin
```

No now i still get:
```
tony@tony:~$ sudo sh yohoho-install.bin
sh: Can't open yohoho-install.bin
tony@tony:~$ 

```

---

### Post by binbash on 2009-01-12
./yohoho-install.bin

---

### Post by kestrel1 on 2009-01-12
I assume you have used cd to get to the correct location of the file.

---

### Post by binbash on 2009-01-12
also chmod +x filename

---

### Post by ltcyco on 2009-01-12
binbash when i get that it gives me an error saying the directory doesnt exist.
And no I just went to the site and downloaded yto desktop  i assumed thats where it was supposed to go?

---

### Post by donkyhotay on 2009-01-12
I've play that game sometimes been awhile since I've had to reinstall it, but as I remember it's a java program not a regular binary so in order to run it you need to do it through java. Can't remember the exact code but I think it's something like 
```
jre ./yohoho
```
or something like that. As I said it's been awhile.

---

### Post by binbash on 2009-01-12
dude i dont know where you downloaded the file but default it should be at Desktop

go to Desktop and give ls command and see the file there, if it is there give the chmod and ./ command i wrote above.If you see any error paste the terminal output so we can help.

---

### Post by kestrel1 on 2009-01-12
Go to a terminal window & type:
```
cd Desktop
```
This will get you to the correct folder if the file is saved on your desktop.

---

### Post by ltcyco on 2009-01-12
When i tried the jre command i got ```
tony@tony:~$ jre ./yohoho
bash: jre: command not found

```

And when i tried the ./yohoho-install.bin command i got
```
tony@tony:~$ ./yohoho-install.bin
bash: ./yohoho-install.bin: No such file or directory
tony@tony:~$ 

```

---

### Post by kestrel1 on 2009-01-12
In the terminal type ```
ls
```
Can you see the file in the list.
If not post what you see.

---

### Post by binbash on 2009-01-12
> **ltcyco said:**
> When i tried the jre command i got ```
tony@tony:~$ jre ./yohoho
bash: jre: command not found

```

And when i tried the ./yohoho-install.bin command i got
```
tony@tony:~$ ./yohoho-install.bin
bash: ./yohoho-install.bin: No such file or directory
tony@tony:~$ 

```


IIt is not Desktop folder!!

cd Desktop

then give the command

---

### Post by ltcyco on 2009-01-12
this is all i got
```
tony@tony:~$ ls
Desktop  Documents  Examples  jagex_runescape_preferences.dat  Music  Pictures  Public  Templates  Untitled.xcf  Videos

```

---

### Post by kestrel1 on 2009-01-12
then type```
cd Desktop
```

---

### Post by ltcyco on 2009-01-12
> **binbash said:**
> IIt is not Desktop folder!!

cd Desktop

then give the command
Well i think im getting closer now i got:
```
tony@tony:~$ cd Desktop
tony@tony:~/Desktop$ ./yohoho-install.bin
bash: ./yohoho-install.bin: Permission denied
tony@tony:~/Desktop$ 

```
Sorry if im missing something really odvious im a total script kiddie especially when it comes to linux ive only had it for  about 2 weeks now

---

### Post by kestrel1 on 2009-01-12
As I said earlier use sudo before the command```
sudo ./yohoho-install.bin

```

---

### Post by ltcyco on 2009-01-12
> **kestrel1 said:**
> As I said earlier use sudo before the command```
sudo ./yohoho-install.bin

```
YES thank you! its working now :D why does linux have to be so complicated xD

---

### Post by kestrel1 on 2009-01-12
It is only complicated until you get used to it.
Once you know how to use the terminal, you will get to like it even more. I promise.

---

### Post by kestrel1 on 2009-01-12
> **ltcyco said:**
> YES thank you! its working now :D why does linux have to be so complicated xD
Can you do us a favour & mark the post as solved please.
To do this go to the top of the post & you should see Thread Tools, click on this & select the correct option from the drop down list.
Thanks

---

