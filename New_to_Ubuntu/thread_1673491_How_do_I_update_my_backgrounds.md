---
title: "How do I update my backgrounds?"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by spydeyrch on 2011-01-22
I recently downloaded some 400 wallpapers for my background. I downloaded them into my Downloads folder. From there, I copied them via the terminal to my /usr/share/backgrounds/ folder using

```

sudo cp ~/Downloads/* /user/share/backgrounds/

```Then when I went to select my backgrounds via the change background option under desktop options, none of them were there. So I figured a restart would update the backgrounds list (if there is one) ..... but that didn't work. So I just used the 'add' button on the background selector window and added my /usr/share/backgrounds/ images from that location. They are now in the background list but I was wondering......

Is there a better way to have the backgrounds list (if there really is one. maybe it is a database of some sorts) update/refresh to include the newly added backgrounds in the folder?

I am afraid that I might have duplicates being that I selected ALL of the images in that folder, and some of them already exsisted previously.

Any ideas? Thanks in advance!!

-Spydey

P.S. the only files/directories in my Downloads folder were the background images.

---

### Post by mikewhatever on 2011-01-22
This part is the problem [s]/user/share/backgrounds/[/s], should be /usr/share/backgrounds/.

It's /usr, and not /user.

---

### Post by spydeyrch on 2011-01-22
my bad, it was a typo. the location that I really did put them in is usr, not user.  It was just a typo on my end. sorry.

Anyway to update the backgrounds?

---

### Post by ibuclaw on 2011-01-22
Right-clicking on the Desktop -> Change Background, then clicking and dragging the images into the window sounds like a good idea to me. :)

---

### Post by coffeecat on 2011-01-22
The list of files that appear in the background tab of the Appearance window are in ~/.gnome2/backgrounds.xml. The only way I know of getting 400 new ones into that file is to drag the images as ibuclaw describes, or edit the xml file yourself.

Have fun! :)

---

### Post by peculiar penguin on 2011-01-22
Another option is running a wallpaper changer application (e.g. DesktopNova), as these usually allow you to define custom wallpaper directories.

---

### Post by spydeyrch on 2011-01-23
I think that what I did was probably the easiest way to do it. Thanks everyone for your input, it is very much appreciated.

I just wish that it would auto update. I am also using desktop drapes and it monitors specified folders. I told it to monitor my /usr/share/backgrounds/ and it seems to be doing a pretty god job so far. Thanks again everyone for your input.

-Spydey

---

### Post by Megaptera on 2011-01-23
I don't know if it's safe or healthy! But when I want to add images to my Backgrounds I download to Pictures. Then in terminal sudo nautilus then go to Pictures > select all > copy     then open home >file system > usr > share > backgrounds and then paste.

Then exit terminal.

---

### Post by ibuclaw on 2011-01-23
> **Megaptera said:**
> I don't know if it's safe or healthy! But when I want to add images to my Backgrounds I download to Pictures. Then in terminal sudo nautilus then go to Pictures > select all > copy     then open home >file system > usr > share > backgrounds and then paste.

Then exit terminal.
The problem with that is you *don't* need **root** privileges to change a **user** setting.

---

### Post by spydeyrch on 2011-01-24
> **Megaptera said:**
> I don't know if it's safe or healthy! But when I want to add images to my Backgrounds I download to Pictures. Then in terminal sudo nautilus then go to Pictures > select all > copy     then open home >file system > usr > share > backgrounds and then paste.

Then exit terminal.

so, that is exactly what I did. The only issue is that if you then right-click on your desktop, select change background, and then browse through the available backgrounds, the new ones that you just cut & pasted into /usr/share/backgrounds are not there. Even after a restart it doesn't register them. The only way that I could get them to "register" after moving them into /usr/share/backgrounds is to right-click on the desktop, select change background, then click on 'add', then browse to the /usr/share/backgrounds folder and selecting all the backgrounds there. It will sort through them and add the new ones while not creating duplicates of the already existing ones. I hope that is clear enough. ;)

[quote=ibuclaw]
The problem with that is you *don't* need **root** privileges to  change a **user** setting. 	
[/quote]

Really? Cause when I tried it without using root privileges, I couldn't get it to work. It wouldn't copy them over for some reason. Granted I didn't use root nautilus to do it, I used the terminal. :D
Any thoughts or insight on this? Thanks. :)

-Spydey

---

### Post by Megaptera on 2011-01-24
I too couldn't get it to work without root but thought that was just me.

Glad you found a work-around spydeyrch.

---

### Post by coffeecat on 2011-01-24
> **spydeyrch said:**
> Really? Cause when I tried it without using root privileges, I couldn't get it to work. It wouldn't copy them over for some reason. Granted I didn't use root nautilus to do it, I used the terminal. :D
Any thoughts or insight on this? Thanks. :)

You need root privileges to copy stuff into a folder in /usr because that is a root-owned part of the system, but you** do not** need root privileges to add more wallpapers to your selection. Simply store your 400 wallpapers somewhere owned by yourself (somewhere in /home or in a data partition to which you have ordinary access) and then drag and drop the ones you need into the Appearances window. Which is what I do.

You only need to store wallpapers in /usr/share/backgrounds/ if you need them accessed by all accounts on the system in which case you obviously need root privileges because that is, by definition, an administrator task.

---

### Post by Megaptera on 2011-01-25
Thanks for the clarification coffeecat.

---

### Post by Ziskille on 2011-01-25
Bahaha I came here thinking I could lend a hand but it looks like you guys have got it sorted! :) Dang I wanna help someone too :p

---

### Post by spydeyrch on 2011-01-25
@coffeecat

Awesome. Thanks for that clarification. I appreciate you help.

@megaptera

Yup, I got it to work. But still, it would be nice to have the system auto-recognize that additional wallpapers were added to the /usr/share/backgrounds/ folder if that is where they are stored.

True, once could do it the way that coffeecat mentioned. Having them stored in a separate folder or partition and just drag-n-drop them into the appearances window, but  I like to have things on my system organized in a certain fashion.

So until I have another issue, thanks again everyone.

@Ziskille

Any input you have is greatly appreciated. Do you have an idea or a thought you wanted to share? Perhaps some different approach to this issue that someone hasn't already mentioned? 

-Spydey

---

