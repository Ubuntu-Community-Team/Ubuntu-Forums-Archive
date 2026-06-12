---
title: "Some Issues/Questions I have in regard to Ubuntu"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by NonStop on 2010-08-30
Just started using Ubuntu 10.04. I currently have the version current graphics driver installed (Nvidia), as well as the Extra setting selected under effects in appearance. Here are my problems:

1) I'm noticing that when I use Facebook, certain images look slightly pixelated, yet if I right-click on them and view the image in a separate page, the image looks fine. How can I fix this?

2) I've set the icons on my desktop to Keep Aligned, but when I reboot the computer, the icons are always scattered around and not aligned, despite the fact the keep aligned option is still ticked.

3) How can I add Rhythmbox, or any other application for that matter, to startup, ie in the top-right hand corner with other startup icons so I can start using it right away.

4) Is it possible to have thumbnails on the folders, like in Windows, so you have pictures of the contents of the folder, which I would find particularly useful for folders with images inside?

Thanks in advance.

---

### Post by migs73 on 2010-08-30
For the Rhythmbox start-up try, System--> Preferences-->Startup Applications click add and set up rhythmbox. 
This might open full screen though and not just the icon on the panel, I've not tried it yet.

Edit; just gave it a bash and works fine, only the icon appears not full screen.
See attached screen shot for what to put in when you go to 'add'

---

### Post by NonStop on 2010-08-30
> **migs73 said:**
> For the Rhythmbox start-up try, System--> Preferences-->Startup Applications click add and set up rhythmbox. 
This might open full screen though and not just the icon on the panel, I've not tried it yet.

Edit; just gave it a bash and works fine, only the icon appears not full screen.
See attached screen shot for what to put in when you go to 'add'

Worked perfectly, thank you very much.

Any other help available for my other questions?

---

### Post by pasti on 2010-08-30
Hello Nonstop

I can help with question 4,
just right click the folder you want to add a thumbnail to,
at the bottom of the menu select "properties", 
then click on the folder icon at the top left of the window that opens, and select whichever image you want from the list, a preview will appear on the right hand side, click "open" at the bottom right and then close the window and  you're done.

I can't help with the facebook question as I never use it, and I get the exact same problem with desktop items as you are, so I tend not to keep things there very long

---

### Post by Jonny87 on 2010-08-30
> 1) I'm noticing that when I use Facebook, certain images look slightly pixelated, yet if I right-click on them and view the image in a separate page, the image looks fine. How can I fix this?

What web browser are you using? Mozzila or have you installed another one? I know the some browsers such as Opera have settings that can be changed to allow faster page loading but as result the picture aren't as clear. Other wise what is your internet connection like, and does it just happen with facebook?

---

### Post by oldsoundguy on 2010-08-30
There is a neat add on for Facebook in FireFox.  It is called "Facebook Photo Zoom" .... after installing all you need do is a mouse over to get the enlarged version of any picture. I like it a LOT!

No clicking unless I want to save the image!

---

### Post by NonStop on 2010-08-31
> **pasti said:**
> Hello Nonstop

I can help with question 4,
just right click the folder you want to add a thumbnail to,
at the bottom of the menu select "properties", 
then click on the folder icon at the top left of the window that opens, and select whichever image you want from the list, a preview will appear on the right hand side, click "open" at the bottom right and then close the window and  you're done.

I can't help with the facebook question as I never use it, and I get the exact same problem with desktop items as you are, so I tend not to keep things there very long

Thank you for the response about the thumbnail. Problem is, I want to do that for hundreds of folders, manually doing each individual folder would take far too long, I just want an automatic thumbnail of images inside like Windows. Is such a feature possible?

The desktop items are a massive annoyance, surely something as basic as the OS remembering settings properly is a basic issue that has to be resolved?


> **Jonny87 said:**
> What web browser are you using? Mozzila or have you installed another one? I know the some browsers such as Opera have settings that can be changed to allow faster page loading but as result the picture aren't as clear. Other wise what is your internet connection like, and does it just happen with facebook?

I am using the latest version of Firefox. However, I figured out the problem myself its because I had the zoom setting on. However, my problem now is that the text is far too small, how can I make it bigger without zooming in and pixelating some images?

---

### Post by migs73 on 2010-08-31
To change the text size in FF, go to Edit--> Preferences and click on the Content Tab. There is a Fonts and Colours section there where you can change the font size.

---

### Post by silverglade00 on 2010-08-31
For your folder icons, you can try this. Open a Nautilus window, your home folder will be perfect. Then go to the Edit menu and choose Preferences. Click on the Preview tab and set Show Thumbnails to Local Files Only or Always. Then make sure the Size limit below it is set to something sane. I just changed mine to 100MB.

---

### Post by coffeecat on 2010-08-31
> **NonStop said:**
> The desktop items are a massive annoyance, surely something as basic as the OS remembering settings properly is a basic issue that has to be resolved?

Agreed, except that something must have gone amiss in your system. I don't think I've ever seen this issue on the forum. I've installed many versions of Ubuntu to several machines over the years, always set the desktop to the default - 'keep aligned' - and never had icons go on walkabouts.

Try unticking the keep aligned option and then reticking it. Apart from that, I haven't got an immediate answer. I need to find in which config file the positions are stored. If I do I'll post back.

---

### Post by NonStop on 2010-08-31
> **migs73 said:**
> To change the text size in FF, go to Edit--> Preferences and click on the Content Tab. There is a Fonts and Colours section there where you can change the font size.

That works perfectly, thank you.

> **silverglade00 said:**
> For your folder icons, you can try this. Open a Nautilus window, your home folder will be perfect. Then go to the Edit menu and choose Preferences. Click on the Preview tab and set Show Thumbnails to Local Files Only or Always. Then make sure the Size limit below it is set to something sane. I just changed mine to 100MB.

Have tried what you said, but to no avail, as the attached screenshot shows, all the folders are just icons with no thumbnails of the images inside, unlike this in Windows; [http://imgsrv.worldstart.com/ct-images/folder-pic-blank1.jpg](http://imgsrv.worldstart.com/ct-images/folder-pic-blank1.jpg)

> **coffeecat said:**
> Agreed, except that something must have gone amiss in your system. I don't think I've ever seen this issue on the forum. I've installed many versions of Ubuntu to several machines over the years, always set the desktop to the default - 'keep aligned' - and never had icons go on walkabouts.

Try unticking the keep aligned option and then reticking it. Apart from that, I haven't got an immediate answer. I need to find in which config file the positions are stored. If I do I'll post back.

Thank you for your time, I do appreciate it. Maybe this has something to do with me wrongly deleting the keyring as shown here (I was getting annoyed with it asking for my old password as my keyring after having changed my normal  password): [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

For now, I have just deleted the icons the desktop, and unticked the Keep aligned setting.

---

### Post by NonStop on 2010-09-02
Any help people?

---

### Post by NonStop on 2010-09-09
Anyone?

---

### Post by migs73 on 2010-09-10
Probably best if you mark this thread as solved and then start new independant ones for your other issues.):P

---

