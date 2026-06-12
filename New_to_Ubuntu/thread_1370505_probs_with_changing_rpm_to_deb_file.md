---
title: "probs with changing rpm to deb file"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by skeebs on 2010-01-02
Hi I've downloaded an rpm file, looked up and followed instructions on how to change it to a deb via "alien" in sudo but when trying it I get "file not found". I'm sure it's something really simple that I'm missing but am new to using linux, any ideas? thanks

---

### Post by HiImTye on 2010-01-02
what command did you use and what was the output

---

### Post by oldos2er on 2010-01-02
You need to run "sudo alien..." in the directory where the *rpm file is.

---

### Post by skeebs on 2010-01-02
I did "sudo alien" followed by a variety of ways to write the route to my file which is on my desktop (eg desktop/my_file_name and home/desktop/my_file_name). I wasn't sure if it had to have a ~ sign in front or not but it didn't make any difference as each time I just get: File "whatever" not found

---

### Post by chaanakya_chiraag on 2010-01-02
The exact code would be (if it is located on the desktop):
```
sudo alien ~/Desktop/your_file_name.rpm
```

---

### Post by skeebs on 2010-01-02
> **oldos2er said:**
> You need to run "sudo alien..." in the directory where the *rpm file is.

Oh I see. How do I run it in the directory of where it is ie my desktop?

---

### Post by Cheesemill on 2010-01-02
If you can't figure out the exact path just type 'sudo alien ' into the terminal and then drag and drop the file into the terminal, it will fill in the path and filename for you.

---

### Post by chaanakya_chiraag on 2010-01-02
Also, you should get used to tab completion.  Type part of the file/folder name and hit the [Tab] key and voila! the shell completes the name.  If there's a noise, hit [Tab] again to see the list of possibilities :)

---

### Post by skeebs on 2010-01-02
> **chaanakya_chiraag said:**
> The exact code would be (if it is located on the desktop):
```
sudo alien ~/Desktop/your_file_name.rpm
```

no just tried that still not found

---

### Post by chaanakya_chiraag on 2010-01-02
Does the rpm's name have spaces in it?

---

### Post by halitech on 2010-01-02
what are you trying to install? there may be an easier way then converting an rpm to deb to get it installed.

---

### Post by chaanakya_chiraag on 2010-01-02
> **halitech said:**
> what are you trying to install? there may be an easier way then converting an rpm to deb to get it installed.
Seconded!

---

### Post by skeebs on 2010-01-02
> **Cheesemill said:**
> If you can't figure out the exact path just type 'sudo alien ' into the terminal and then drag and drop the file into the terminal, it will fill in the path and filename for you.


oh that's quicker but now I've got "unknown type of package"

Is alien meant to automatically convert the file or am I meant to tell it to do this while telling it where to find the file?

---

### Post by chaanakya_chiraag on 2010-01-02
Are you sure it's an rpm?  Because alien should automatically convert it :)

---

### Post by skeebs on 2010-01-02
> **chaanakya_chiraag said:**
> Does the rpm's name have spaces in it?

no

---

### Post by chaanakya_chiraag on 2010-01-02
Which program are you trying to install?

---

### Post by skeebs on 2010-01-02
> **halitech said:**
> what are you trying to install? there may be an easier way then converting an rpm to deb to get it installed.

it's a language learning program that's free to download. The options were to download in various windows, mac and unix so I chose unix. Might be rubbish anyway after all this!! :)

---

### Post by halitech on 2010-01-02
do you have a link to where you downloaded the file from?

---

### Post by skeebs on 2010-01-02
> **chaanakya_chiraag said:**
> Are you sure it's an rpm?  Because alien should automatically convert it :)

oh it's got a .bin in it. Sorry, just focused on the rpm. So it's rpm.bin... what does that mean? Does that change this whole mission??

---

### Post by chaanakya_chiraag on 2010-01-02
That means you just run the file like this:
```
sudo ~/Desktop/your_file_name.rpm.bin
```

---

### Post by skeebs on 2010-01-02
> **halitech said:**
> do you have a link to where you downloaded the file from?

[http://foundationstone.com.au/FoundationStone.html?./OnlineHebrewTutorial.html](http://foundationstone.com.au/FoundationStone.html?./OnlineHebrewTutorial.html)

go to downloads and you'll see the options of what format you want it in

---

### Post by skeebs on 2010-01-02
> **chaanakya_chiraag said:**
> That means you just run the file like this:
```
sudo ~/Desktop/your_file_name.rpm.bin
```

yeah done that in my earlier attempts :(

---

### Post by halitech on 2010-01-02
> **skeebs said:**
> [http://foundationstone.com.au/FoundationStone.html?./OnlineHebrewTutorial.html](http://foundationstone.com.au/FoundationStone.html?./OnlineHebrewTutorial.html)

go to downloads and you'll see the options of what format you want it in

I downloaded version 4.0 for Unix and got a tar.gz file. I extracted that and I got a file called foundationStone.sh that should run in the terminal

update: I ran ~/downloads/FoundationStone_4.0/foundationStone.sh and it loaded fine. (~/downloads is where I save everything and it extracted to FoundationStone_4.0)

---

### Post by skeebs on 2010-01-02
how come you got a different file? Mine came as that rpm.bin

Shall I try downloading it again then :confused:

---

### Post by halitech on 2010-01-02
> **skeebs said:**
> how come you got a different file? Mine came as that rpm.bin

Shall I try downloading it again then :confused:

I would and make sure it is a tar.gz file that you are downloading.

---

### Post by skeebs on 2010-01-02
ok, here goes...

Thanks loads and loads for your help (and to everyone else) :) if this doesn't work I'll prob just cry and then try finding something else!!

---

### Post by skeebs on 2010-01-02
> **halitech said:**
> I downloaded version 4.0 for Unix and got a tar.gz file. I extracted that and I got a file called foundationStone.sh that should run in the terminal

update: I ran ~/downloads/FoundationStone_4.0/foundationStone.sh and it loaded fine. (~/downloads is where I save everything and it extracted to FoundationStone_4.0)

seems to be working now nice one!! Yeah I think it didn't download properly first time or something as I defo have a different file on my desktop this time round. Thanks again for your time and help :):):)

---

### Post by halitech on 2010-01-02
glad to hear its working for you :)

---

### Post by chaanakya_chiraag on 2010-01-02
YAY!!!!!  Good for you!!!! :)  Yet one more satisfied Ubuntu user :D

---

### Post by chaanakya_chiraag on 2010-01-02
Please mark the thread solved so that others can learn from this experience.  Thanks :)

---

