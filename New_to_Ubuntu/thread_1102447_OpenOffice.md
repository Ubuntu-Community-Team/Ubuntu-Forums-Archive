---
title: "OpenOffice"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Riff-raff on 2009-03-21
Ok i have taken the leap of faith into installing Ubuntu onto my Desktop.
 Only problem that i've encountered is in Openoffice.

In all the Openoffice programs when opened there is "Text" missing from the application window. As in File, Edit, View ect. Even when the cursor hovers over where the word should be a small box appears and shows the missing word for a nano second. Also if i click where the "File" should be the cascaded list appears but again with no words like save, save as, send to. ect

Sorry if i haven't explained it very well but i'm sure someone can understand my query.

Oh one other thing, Openoffice opens Microsoft word documents but how can i open an Openoffice document using Microsoft word?

---

### Post by The Cog on 2009-03-21
I have seen the blank menus that you describe. I don't remember which application as I haven't seen it for a few years. I think it's down to video drivers. What make of video card to you have? Maybe using proprietary drivers will make it work. If you are using the 3d desktop effects, you could try tuning them off.

OOo can save files in MS Office format - use File - Save As...
Alternatively, Sun do a plugin that allows office to read ODF files. Microsoft themselves don't, of course. They don't approve of standards.
[http://www.sun.com/software/star/odf_plugin/get.jsp](http://www.sun.com/software/star/odf_plugin/get.jsp)

---

### Post by eilios on 2009-03-21
> **Riff-raff said:**
> Ok i have taken the leap of faith into installing Ubuntu onto my Desktop.
 Only problem that i've encountered is in Openoffice.

In all the Openoffice programs when opened there is "Text" missing from the application window. As in File, Edit, View ect. Even when the cursor hovers over where the word should be a small box appears and shows the missing word for a nano second. Also if i click where the "File" should be the cascaded list appears but again with no words like save, save as, send to. ect

Sorry if i haven't explained it very well but i'm sure someone can understand my query.

Oh one other thing, Openoffice opens Microsoft word documents but how can i open an Openoffice document using Microsoft word?
Save it as a microsoft word document.

---

### Post by Riff-raff on 2009-03-22
Mmm graphics card, i'll have to go into that one to find out as it's quite old now.
 The file menu systems work in the other applications like email, but i'll have a play on my desktop when i have time later.

 As for saving it as a word document, if the file system works i'll try it but it's not easy guessing from a list of nothing which one is "Save as"

 So if i get my original problem sorted i should be fine.... Now just to get the headers and menu systems working...

Many thanks so far for your time in responding.

---

### Post by Bearly Able on 2009-03-22
Ctrl + Shift + S will open the "Save As" dialogue.

---

### Post by gandaran on 2009-03-22
> **Riff-raff said:**
> Ok i have taken the leap of faith into installing Ubuntu onto my Desktop.
 Only problem that i've encountered is in Openoffice.

In all the Openoffice programs when opened there is "Text" missing from the application window. As in File, Edit, View ect. Even when the cursor hovers over where the word should be a small box appears and shows the missing word for a nano second. Also if i click where the "File" should be the cascaded list appears but again with no words like save, save as, send to. ect

Sorry if i haven't explained it very well but i'm sure someone can understand my query.

Oh one other thing, Openoffice opens Microsoft word documents but how can i open an Openoffice document using Microsoft word?

try a deferent GKT theme

---

### Post by The Cog on 2009-03-22
> **gandaran said:**
> try a deferent GKT theme

Now you say it, that rings a bell. It may well be the theme, or the application fonts chosen. Well worth a try!

---

### Post by Riff-raff on 2009-03-22
> **gandaran said:**
> try a deferent GKT theme

Ok sounds like an idea, but being green as grass.... How do i change the GKT theme? Guide me in please.

---

### Post by roger_1960 on 2009-03-22
Hi

system - preferences - appearance and the theme tab.

---

### Post by eilios on 2009-03-22
> **Riff-raff said:**
> Ok sounds like an idea, but being green as grass.... How do i change the GKT theme? Guide me in please.
Step 1: System, preferences
Step 2: Appearence
Step 3: Mod the theme as you will. It's pretty simple and very fun.

---

### Post by fcuk112 on 2009-03-22
what happens if you open up a terminal window and type the following?

```

metacity --replace

```

---

### Post by fcuk112 on 2009-03-22
you can also try upgrading to openoffice 3.0:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by Riff-raff on 2009-03-23
> **fcuk112 said:**
> what happens if you open up a terminal window and type the following?

```

metacity --replace

```

 First i had to learn how to open a terminal window. I used Alt+F2 then typed xterm

Anyway i tried Metacity --replace

I opened openoffice and the file system now works :popcorn:

But i couldn't or didn't know how to make it full screen. Nore did the change screen thingy work (By the recycle bin icon)

So i restarted the pc and it all went back to it's previous form with the file system not working again in open office. So how do i fix it or do i as you also suggested download a later version of open office.

Many thanks for helping.

Andy

---

### Post by Riff-raff on 2009-03-23
> **The Cog said:**
> I have seen the blank menus that you describe. I don't remember which application as I haven't seen it for a few years. I think it's down to video drivers. What make of video card to you have? Maybe using proprietary drivers will make it work. If you are using the 3d desktop effects, you could try tuning them off.

OOo can save files in MS Office format - use File - Save As...
Alternatively, Sun do a plugin that allows office to read ODF files. Microsoft themselves don't, of course. They don't approve of standards.
[http://www.sun.com/software/star/odf_plugin/get.jsp](http://www.sun.com/software/star/odf_plugin/get.jsp)

Sorry only just got round to finding the graphics card spec, its Nvidia Geforce MX440 with AGP8X

---

### Post by jimv on 2009-03-23
Try this.  Go to  System > Preferences > Appearance, and click the Visual Effects tab.  Set it to None.  Close the window and try Open Office again.

---

### Post by Riff-raff on 2009-03-24
> **jimv said:**
> Try this.  Go to  System > Preferences > Appearance, and click the Visual Effects tab.  Set it to None.  Close the window and try Open Office again.

Jim, just tried it.When set to none it all worked fine. Then to double check i changed it back again and it then failed to show again.

---

### Post by jimv on 2009-03-24
Well, if you don't care about desktop effects (Compiz) you could just leave it off.

If you do want the desktop effects, I'd make a new thread in the Desktop Environments forum and say something like "Text in OpenOffice menus disappears when Compiz is enabled."

---

