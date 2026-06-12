---
title: "3d cairo dock &amp; make terminal non-transparent"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by hollowtd on 2009-02-19
Thanks for reading these two quick questions:

1. I have just installed Cario dock on my ubuntu 8.10. I have seen and done all sorts of research to get it to run 3d. Maybe I don't know what I'm talking about, but is this possible and how?

2. I turned my terminal transparent. I know there is the default setting to get it back to normal. Does anyone know how to do this? 



Cheers and though I know Ubuntu, I'm still learning all the "talk" so be easy on my virgin linux. Cheers in advance

---

### Post by NESFreak on 2009-02-19
> **hollowtd said:**
> Thanks for reading these two quick questions:

1. I have just installed Cario dock on my ubuntu 8.10. I have seen and done all sorts of research to get it to run 3d. Maybe I don't know what I'm talking about, but is this possible and how?

2. I turned my terminal transparent. I know there is the default setting to get it back to normal. Does anyone know how to do this? 



Cheers and though I know Ubuntu, I'm still learning all the "talk" so be easy on my virgin linux. Cheers in advance

2. in gnome-terminal go to edit-->profilepreferences (or something, translated)-->background rest should point itself

don't know about cairo dock

---

### Post by hollowtd on 2009-02-19
that's the problem I think. The terminal doesn't have the file, edit, and menu titles on top in the bar. There is only the minimize and X close box. How do I get to Edit now?

---

### Post by kestrel1 on 2009-02-19
Could you post a screen shot of what you mean?
I use & configure cairo-dock, so might be able to help.

---

### Post by hollowtd on 2009-02-19
I will post it. Give me  a couple mintues to get on my Linux computer. Thanks

---

### Post by hollowtd on 2009-02-19
I have the file downloaded now called rendering. I have extracted it on my desktop but don't know how to navigate to the folder in terminal. CAn you tell me how? Then I might have it.

---

### Post by kestrel1 on 2009-02-19
To navigate to a folder i.e. Desktop type the following:```
cd Desktop
```
remember that in Linux directory & file names are case sensitive, so if the directory/file says Desktop you must type Desktop & not desktop when trying to cd to it or do anything to a file.

---

### Post by hollowtd on 2009-02-19
I am in the desktop now. I need to get to the Rendering extracted folder that is now on my desktop. I'm looking up commands but can't find out how to navigate to the folder. The terminal line now says :~Desktop$

---

### Post by kestrel1 on 2009-02-19
OK, if the folder is called Rendering type:```
cd Rendering
```
To check what is in a folder type```
ls
```
You could have saved some typing by typing ```
cd Desktop/Rendering
```

---

### Post by hollowtd on 2009-02-19
Thanks for the help. I'm in the ~/Desktop/rendering  and now I want to install those files, but the command Im typing doesn't do it. Not sure what to do now. I type "autoreconf -isvf && ./configure --prefix=/usr/local && make" (I got this from one of the forums)

---

### Post by kestrel1 on 2009-02-19
What are you trying to install here?
If it is to do with Cairo-Dock you don't need to go through all of this.
To install Cairo-dock & the plugins go to this link & follow the instructions:
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by hollowtd on 2009-02-19
Im just having problems installing the contents of the rendering folder from terminal. I just don't know what to type. I've tried the sudo dpkg mehtod and get nothing. I'm just a newbie and have a lot of trouble still. Thanks for the help though, you have been great.

---

### Post by fabounet on 2009-02-20
don't bother compiling it, just install the whole dock+plug-ins through the official repository in 1 click.

---

### Post by kestrel1 on 2009-02-20
Just go to the link I gave earlier in the thread & follow the instructions, there is no need to complie a thing.

---

