---
title: "Mailpictures question"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-24
I've installed and attempting to use "Mailpictures-0.95" to resize picture settings to send to evolution or thunderbird mail.

I'm not quite sure how mailpictures works, but it does not matter to me if it works from inside the email software [evolution or thunderbird] or I do something and right click and it does it work [resizes pics] before it then send it to Evolution or Thunderbird.

My problem is very basic which is I don't know how to get it to work either way - lol


According to the description, mailpictures will "Direct access in nautilus via the context menu Automatic resizing of pictures Setting for jpg compression ZIP archiving of the selection Evolution, Thunderbird, Kmail email attachment Save result in a folder"

I don't even know what a Nautilus window is, so perhaps why I  can't get it to work is because I'm not accessing the pic files in a nautilus window?

please help - confused here.  My goal is to select [highlight] a bunch of pics and resize them before emailing OR add a bunch of pics to Evolution or Thunderbird as attachments to be emailed and mailpictures resizes them somehow before me sending the email to someone.

---

### Post by dj-toonz on 2009-10-24
Well, surfing the net I found this tip to add resize & rotate image functions to nautilus

1.- Open a Terminal

accessories> Terminal or Terminator

2.- Type:

sudo apt-get install nautilus-image-converter

[Enter your password if asked]

3.- Restart Gnome

CTRL + ALT +Backspace

4.- Log in and go to any image folder

5.- Right Click on the image and you wil find two new options

1. Resize
2. Rotate 

Hope that helps

---

### Post by mjp29 on 2009-10-24
> **dj-toonz said:**
> Well, surfing the net I found this tip to add resize & rotate image functions to nautilus

1.- Open a Terminal

accessories> Terminal or Terminator

2.- Type:

sudo apt-get install nautilus-image-converter

[Enter your password if asked]

3.- Restart Gnome

CTRL + ALT +Backspace

4.- Log in and go to any image folder

5.- Right Click on the image and you wil find two new options

1. Resize
2. Rotate 

Hope that helps


So, in theory, I can type this into terminal ->sudo apt-get install nautilus-image-converter

However, what does "restart Gnome mean"?

Then, open a folder that has a lot of .jpg images in it and highlight or select all many images

Then, right click on any of the many selected .jpg files and have the option to resize

My concerns are this:  I don't want to resize the actual image - I want to preserver the size of the original image.  I only want mailpictures to temporarily resize the image for emailing only

---

### Post by misfitpierce on 2009-10-24
You might need to logout to restart gnome... as I think the CTRL+ALT+BKSPC thing does not work by default in jaunty unless you have the xserver-kill thing installed in order to enable it. It just means restart xserver and can be done by logging out or restarting if all methods fail... but a logout will do!

---

### Post by dj-toonz on 2009-10-24
Nautilus doesn't resize the real image (it makes a temporary or back up file from the file what you click on) so the file you have been working with doesn't get touched if that makes sense

& gnome is the desktop of Ubuntu, KDE is the desktop of Kubuntu & XFCE is the desktop of xubuntu

---

### Post by mjp29 on 2009-10-24
> **dj-toonz said:**
> Well, surfing the net I found this tip to add resize & rotate image functions to nautilus

1.- Open a Terminal

accessories> Terminal or Terminator

2.- Type:

sudo apt-get install nautilus-image-converter

[Enter your password if asked]

3.- Restart Gnome

CTRL + ALT +Backspace

4.- Log in and go to any image folder

5.- Right Click on the image and you wil find two new options

1. Resize
2. Rotate 

Hope that helps

This is awesome.  I did exactly what you said and restarted the computer.  Now I can select all photos in a folder (or select certain photos in a folder) and resize them instantly.

I would like to make one not for the users that read this post in the future which is very important:  If you want to simply email resized photos then you don't want to right click and then select resize.  You actually want to right click on all your highlighted photos and select "send by mail"  

By right clicking a group of photos and then choosing "send by mail", mailpictures will then give you a pop up screen (which by default is set to 640 picture width and 85 jpeg compression which both are excellent for emailing).  However, if you choose, you can from that pop up screen change your desired specs on picture width and jpg compression.  Once you select what you want (I just chose use current settings which is 640 pic width and 85 jpg compression) then it is sent on to your email client (evolution or thunderbird or whatever your defaults email is), it sends it on to your email program without you having to do anything - quite a very nice trick and very very nice way to email photos on the fly!

Other note:  If you are doing this, like I want to, which is to resize photos on the fly for emailing then do not choose "resize" when you right click a bunch of selected photos because then it will resize all those photos and save a resized file next to the original in the folder.  What you really want mailpictures to do [if using it to email like i am] is to just resize them on the fly and not save any resized files next to the originals and just resize them on the fly, send the resized image to your mail program, and then type in the email address and subject of your receiver and hit send.

But one could use mailpictures to resize images (right clicking) to save a resized image next to each original if that is your goal.  But this post is all about emailing resized photos on the fly.

Excellent!

I'm marking this post SOLVED

thank you thank you thank you

---

### Post by dj-toonz on 2009-10-24
Your welcome, Glad I could Help :-)) :guitar:

---

### Post by mjp29 on 2009-10-24
Thank you and it worked and I love it.  Mailpictures rocks!

Curious questions: 

1- Is Mailpictures an app, a program, an add on, or how would you classify it?
2- So Gnome, according to other poster and you, Gnome is actually the "desktop" of Ubuntu o.s., right?
3 - What is Nautilus?  Mailpictures isn't "Nautilus" is it?  Just trying to understand terminology here.



Thanks so much!

---

### Post by mjp29 on 2009-10-24
Got it to work and it works great!

Curious question:  What is "Nautilus" ?

My understanding now is that Gnome is the desktop of Ubuntu.

But surely "Nautilus" isn't the same as "mailpictures" 

?

just trying to understand the terminology of using a different (and much much better) operating system

---

### Post by avacado on 2010-01-03
Cut and paste
sudo apt-get install nautilus-image-converter


For definition of Nautilus see thread 438504

---

