---
title: "New user, list of issues"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by AaronCodyE on 2009-06-19
Well, I've used windows all my life, and switching has been a battle, but I really want to use linux and ubuntu seemed like a good place to start.

Anyway, I need a lot of help, first of all, it refuses to recognize my cd and dvd drives, saying that there is no media in them even when I do have cd's/dvds in them. Second, and possibly most important, I have tried to solve a few of these problems myself, but all of the solutions involve entering some sort of code, and to be completely honest I have no idea where to enter this code or anything. 

Third, I can't watch youtube videos because I don't have the latest adobe flash player, and when I download it it says "Error, wrong architecture 'i86'". Finally, the peculiar thing about the cd/dvd driver issue is that it will recognize the ubuntu live cd, but it will not recognize anything else.

I realize I must seem like an idiot, but I'm dedicated to learning a new OS, and I thank you all for any help you have to offer.

---

### Post by Michael.Godawski on 2009-06-19
hi,

you are not an idiot. You are just in an new alien environment. 

To "use" the code, you have to enter it into the terminal.
Applications > Accessories > Terminal

To solve the media issue, I would install the package called ubuntu-restricted-extras. It contains the most needed codecs, and stuff like java and flash and many more useful things.

So go to the terminal and run:

```
sudo apt-get install ubuntu-restricted-extras
```Type in your login password, which won't be displayed (for security reasons).

---

### Post by lyni on 2009-06-19
hi its not unusual to feel like you're floundering when you do something new. have a look at the information in the links in my signature. they might help to familiarise yourself to a new system.

---

### Post by AaronCodyE on 2009-06-19
I did what you said, it let me download adobe flash player 10 (the tar.gz one if it matters) but I can't figure out how to install it, also, now at least I know how to use terminal, so thank you.

Also lyni, thank you for those links, they really helped!

---

### Post by nothingspecial on 2009-06-19
If you installed the ubuntu-restricted-extras package you should have flash. You don`t need to install the tar.gz package.

---

### Post by AaronCodyE on 2009-06-19
Hmm, it still wont let me view youtube videos

---

### Post by nothingspecial on 2009-06-19
Have a look [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

This should solve most of your issues. 

Just do the bits appropriate for your ubuntu version.

---

### Post by htzzz on 2009-06-19
are you using x86_64 system?

---

### Post by AaronCodyE on 2009-06-19
I am honestly not sure, but youtube works now, and I forgot to mention earlier that my speakers aren't working.

---

### Post by nothingspecial on 2009-06-19
Well the first thing to do is to click on the volume icon in your panel and check everything is turned up.

Do you know what sound card you have?

---

### Post by AaronCodyE on 2009-06-19
No, it's actually pretty late where I am, so I'm going to go to bed, I will check on all of that and get back to you guys tomorrow, thanks for your help!

---

### Post by dyingsun on 2009-06-19
Congrats on giving it a whirl! Ubuntu is wonderfully addictive, and does everything you need.

You'll save yourself a heap of trouble knowing what hardware and software you're running..

if you type ```
uname -a
```  it should tell you what version of Ubuntu youre running. Pay particular attention to whether it says x86 or x86_64

Also, type this into your terminal:  ```
sudo lshw
```
and keep a copy of the output, it will probably come in handy later on. What does it say in the CPU section? Your CPU should match your Ubuntu version, preferably - you can't run x86_64 bit Ubuntu on a 32-bit architecture.

So make sure you know what you're working with, and it'll make the process of setting up a lot easier, and will also make it easier for the awesomely helpful people in these forums! (Don't know what I'd do without these guys!)

---

### Post by AaronCodyE on 2009-06-19
Well my speakers work now, turns out that big, huge power cable came unplugged AGAIN (probably should have checked that first...whoops) and I'm running the x86_64 bit version of Ubuntu.

Only problems I still seem to be having are installing gfire (need that for pidgin) and getting my dvd/cd drviers to work

---

### Post by scrooge_74 on 2009-06-19
To be a noob in linux land, the wonder of discoveries, the pain and frustration. my two cents here, maybe three.

1. Have patience
2. Don be afraid to ask, most peoeple around here started like you at some point.
3. Check the help page [http://help.ubuntu.com/](http://help.ubuntu.com/)
4. Start to bookmark those pages that prove usefull, you could even make a blog so you can keep handy what you do and latter share the knowledge

---

### Post by scrooge_74 on 2009-06-19
> **AaronCodyE said:**
> Well my speakers work now, turns out that big, huge power cable came unplugged AGAIN (probably should have checked that first...whoops) and I'm running the x86_64 bit version of Ubuntu.

Only problems I still seem to be having are installing gfire (need that for pidgin) and getting my dvd/cd drviers to work

Gfire you need to go to their website and download the deb package.

Remember Ubuntu comes from debian and as in debian you install most apps by downloading a deb package as they are call, other distros use RPM or you may need to compile your own. But if you said you using 64 bit then go for the 64 bit deb package.

For the cd/dvd open a console and after inserting a disc, type dmesg and copy the last few lines maybe there is something for those who know more than me ;)


For your DVD problems, check this: [https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

---

### Post by AaronCodyE on 2009-06-19
Okay, gfire installed, but I can't find it in pidgin or anywhere else

---

### Post by AaronCodyE on 2009-06-19
Well that is working now but youtube videos are laggy, any idea how to fix this?

---

### Post by scrooge_74 on 2009-06-19
I just pause them till they are a bit ahead of the actual point the video is, sometimes I dont have to

---

### Post by AaronCodyE on 2009-06-19
No the video has fully loaded, but it is playing frame by frame, and slower than it should.

---

### Post by scrooge_74 on 2009-06-19
Take a look here [https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html#video-playback-streaming](https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html#video-playback-streaming)

You may still need to set a few things

---

### Post by dyingsun on 2009-06-19
Can you watch video files locally with no problems?

try downloading a Youtube video with clive, for example: 


```
clive http://www.youtube.com/watch?v=Ke-kel9zOFo
```

This saves the Youtube video as a .flv file, I think it defaults to your /home directory. You should be able to run it by double-clicking, or maybe opening it in a browser, or you can convert it to an avi or something like that, with a conversion program. It may help to know if the problem only affects things on the internet, or if your local files are stuffing up too.

---

### Post by AaronCodyE on 2009-06-19
Alright, I've got everything working now, thanks everyone!

---

