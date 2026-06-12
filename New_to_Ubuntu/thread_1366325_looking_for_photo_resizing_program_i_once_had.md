---
title: "looking for photo resizing program i once had"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by mickeyjoe on 2009-12-28
I reinstalled Ubuntu, now I'm looking for a photo resizing program I once had.  Someone on these forums pointed it out to me and it worked like a charm.  Here's how it worked:

When I select many photos and then right click to send the photos to email, Ubuntu would resize the photos so that the email client program would send the emails at a smaller file size.  By default, I think it would resize them to around 800 [either pixels or dpi or something but one could change it on the fly].

Anyways, I need to find the program and reinstall it.  It is a handy program and I don't think I can live without it!

---

### Post by lotharmat on 2009-12-28
```
sudo apt-get install gthumb
```

quite a cool program - apparently it will replace f-spot!

---

### Post by philinux on 2009-12-28
> **mickeyjoe said:**
> I reinstalled Ubuntu, now I'm looking for a photo resizing program I once had.  Someone on these forums pointed it out to me and it worked like a charm.  Here's how it worked:

When I select many photos and then right click to send the photos to email, Ubuntu would resize the photos so that the email client program would send the emails at a smaller file size.  By default, I think it would resize them to around 800 [either pixels or dpi or something but one could change it on the fly].

Anyways, I need to find the program and reinstall it.  It is a handy program and I don't think I can live without it!

Open synaptic, and click on search for photo.

It maybe gnome-photo-printer or gnome-we-photo.

---

### Post by mickeyjoe on 2009-12-28
> **philinux said:**
> Open synaptic, and click on search for photo.

It maybe gnome-photo-printer or gnome-we-photo.


whatever the program is, someone linked to it here on ubuntu and it has a page complete with screenshots and instructions i do believe

---

### Post by mickeyjoe on 2009-12-28
ok thanks

---

### Post by mickeyjoe on 2009-12-29
> **lotharmat said:**
> ```
sudo apt-get install gthumb
```quite a cool program - apparently it will replace f-spot!

I pasted the command into terminal and all seemed to go well; however, I am not getting the same results as I did on the other box. 

This is what I use to get.  What use to happen is this:  When I would select a group of photos (when I would highlight many photos) and then right click, I would get a special selection to "email" photos and inside that it would be pre-selected to resize the photos to 800 size and send it on to my thundermail program.  

Perhaps my problem is my Dell laptop computer I am now working on - ?

---

### Post by mickeyjoe on 2009-12-29
> **lotharmat said:**
> ```
sudo apt-get install gthumb
```quite a cool program - apparently it will replace f-spot!

How do I undo this command, I found the program I want is something called mailpictures.

---

### Post by Ducatiboy Stu on 2009-12-29
sudo apt-get remove gthumb

---

### Post by mickeyjoe on 2009-12-29
> **Ducatiboy Stu said:**
> sudo apt-get remove gthumb


thanks, removed it.


For anyone that wants what I was looking for, I was looking for "mailpictures."

by the way, what does this "gthumb" do?

---

