---
title: "Newbie needs some help."
date: 2009-08-17
forum: New to Ubuntu
---

### Post by gemma.laming on 2009-08-17
Good morning everybody, you can see my name so there is no need to repeat that.

I have recently installed the newest version of Ubuntu on my Lenovo laptop, and my laptop works better now than it did when I used Vista.  I liked the idea of a neat, compact OS that did what I needed (not much) and is made by nice people who are willing to give it to not-very-rich people like me.  

I am having problems installing applications using the terminal window, I have tried to install Kompozer, which I downloaded (and tried again and now cannot, I don't know why I can't, but it just won't) but the sudo apt-get whatever it is just says that it cannot find it.  

Just what am I doing wrong here?  I thought the idea of Linux was that it was easy to use?  I am finding it impossible!  

I still have Kompozer on my download list, twice in fact, but I just can't do anything with it.

Any help would be most appreciated.  Gem

---

### Post by Viva on 2009-08-17
[Install kompozer]("apt:kompozer")

You don't need to use the terminal to install software, unless you're trying to compile stuff yourself. Most of the software you'll need is available through Add/Remove or Synaptic Package Manager

---

### Post by nhasian on 2009-08-17
yep it doesnt get much easier than clicking on a link in your web browser to start installing the software.

you should also read: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by gemma.laming on 2009-08-17
There are times I just feel so dumb.   I tried in desparation to use the sudo apt thingy with just the command Kompozer, and it worked.  

Sometimes computers want all the squiggly stuff at the end of a file name, and sometimes they don't.  Anyway, it's there now, thank goodness.

I was really pleased to see the GIMP ready installed - that was a real treat.  

Thanks.  Gem

---

### Post by nhasian on 2009-08-17
with terminal commands they have to be pretty precise.  you should get into the habit of copy and pasting the commands from websites into the terminal.  copy the text by highlighting it and pressing control-c or right clicking the mouse and saying copy.  then in the terminal simply press Shift-Insert to paste.

```
sudo apt-get install kompozer
```

---

### Post by gemma.laming on 2009-08-18
Thanks, Nhasian,

that is what I tried in desparation - I had tried "kompozer + whatever the extension code was" (I can't open the archive manager, I don't know how) and the system said it could not find it - which I found puzzling.  

Having tried the command "Kompozer" without the extension, and find it to work I found dep;y puzzling.  I thought computers liked all the numbery bits!  

No wonder I keep getting it wrong, when the world is upside down (that is to say, the one I actually live in).

Thankyou for your response, Gem

---

### Post by dilb on 2009-08-18
You can use tab to autocomplete commands in the terminal. So, for example, typing

sudo apt-get install komp

and pressing tab will problably complete the line for you (depending on what software you have available). If you don't get anything, press tab a second time to get a list of options. This also helps make sure you enter the command properly.

---

### Post by 3rdalbum on 2009-08-18
> **gemma.laming said:**
> Thanks, Nhasian,

that is what I tried in desparation - I had tried "kompozer + whatever the extension code was" (I can't open the archive manager, I don't know how) and the system said it could not find it - which I found puzzling.  

Having tried the command "Kompozer" without the extension, and find it to work I found dep;y puzzling.  I thought computers liked all the numbery bits!  

Well, here's a couple of notes that might clear things up for you:

1. When you ran the "sudo apt-get install kompozer", it actually downloaded and installed the software from its own software repositories. This is the best and easiest way to install software...

2. ...except for Synaptic Package Manager. This program is available in System > Administration, and allows you to use a GUI to install any software from the repositories.

3. Apt-get and Synaptic work with their own software repositories, not with software that you've downloaded off the web manually. That's why putting "sudo apt-get install kompozer.tar.gz" doesn't do anything.

---

