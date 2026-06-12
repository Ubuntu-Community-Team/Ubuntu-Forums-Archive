---
title: "JDarkroom help"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by rs87424 on 2011-01-26
here is the website I found this at [http://www.codealchemists.com/jdarkroom/](http://www.codealchemists.com/jdarkroom/)

Hey linux users, I was trying to see if I could find a program to take notes for class with and/or just have a way of typing without any distractions. I found "writer" on the internet but I wanted to use something that didn't need internet access. So I came across darkroom.

I found this with the tips section of the download page:
Ubuntu Linux (or Xandros) users: JDarkRoom will work on Ubuntu/Xandros with Java 1.6. You will need to add the following line to your conf/jdarkroom.properties file (create one if it doesn't exist):
```
suppress.native.look.and.feel=true
```
If that doesn't work (and you're using Ubuntu Gutsy) try adding:
```
force.full.screen=true
```

I was having trouble with finding the conf/jdarkroom.properties file and I don't know where to add a new created file. I need a little help installing this application... I am currently using ubuntu Maverick 10.10

---

### Post by lykeion on 2011-01-26
Tested the app but to me it was just a simple text editor in fullscreen mode. Personally I prefer vim as a text editor. 
There's no installation of jdarkroom, just download it and launch it from a terminal (Applications > Accessories > Terminal)

1. in terminal change to dir where you downloaded the jar-file
```
cd <download_dir>
```
2. launch the app
```
java -jar JDarkRoom.jar
```
If you need to manually edit the jdarkroom.properties file it's located in ~/.jdarkroom/jdarkroom.properties
(the ~ is a shortcut name for /home/<your_username>)

---

### Post by rs87424 on 2011-01-27
Hey lykeion,

I have the jar file stored at ~/Downloads and it said that permission was denied. Also for some reason it keeps saying there is no such file or directory. Should I try to change the file any? I don't know why this is giving me trouble

---

### Post by rs87424 on 2011-01-27
ok, never mind I found out what I was doing wrong

I just kept going to a specific file instead of just going to the directory... I don't know why I make things complicated LOL

---

