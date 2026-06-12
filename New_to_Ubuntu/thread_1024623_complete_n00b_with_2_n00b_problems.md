---
title: "complete n00b with 2 n00b problems"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Mr N00b on 2008-12-29
Hi just have two problems. I have just installed ubuntu dont know anything about it. Have done lots of reading but i'm still scratching my head. How do i install VLC? also ubuntu doesnt allow me access to my external hard drive. cannot mount volume. unable to mount the voulme.


anybody who has the time to help me learn without me getting a headache like i have now will be much appreaciated.


thanks

---

### Post by wmoore on 2008-12-29
To install VLC, open up a terminal and type:```
sudo apt-get install vlc
```
Is your external drive formatted as NTFS by any chance? Can you be a bit more descriptive with the error message?

---

### Post by Mr N00b on 2008-12-29
> **wmoore said:**
> To install VLC, open up a terminal and type:```
sudo apt-get install vlc
```
Is your external drive formatted as NTFS by any chance? Can you be a bit more descriptive with the error message?

Hi thank you i have just learned what the terminal icon was for now i have installed VLC :D

the hard drive error message i get is this:

[IMG]http://img.photobucket.com/albums/v228/nick_w/Screenshot.png[/IMG]

---

### Post by TomasJancik on 2008-12-29
you can also use Synaptic to install software, for beginers it's better because it has GUI (graphical user interface)...

---

### Post by Abu_Dayya on 2008-12-29
I think the solution is in the error message itself if you read it

either:
- connect the external drive in a windows machine and then insure that you "safely remove drive". This has happened to me before, and this is  what i did to solve it

- you can also type the specified command in the terminal. I cant acctually see the error message vividly, I don't have my glasses near me

---

### Post by Abu_Dayya on 2008-12-29
P.S: you wallpaper is realy nice. Where did you get it from? Can you post a link?

---

### Post by Mr N00b on 2008-12-29
> **Abu_Dayya said:**
> I think the solution is in the error message itself if you read it

either:
- connect the external drive in a windows machine and then insure that you "safely remove drive". This has happened to me before, and this is  what i did to solve it

- you can also type the specified command in the terminal. I cant acctually see the error message vividly, I don't have my glasses near me

> **Abu_Dayya said:**
> P.S: you wallpaper is realy nice. Where did you get it from? Can you post a link?

what do you mean safley remove drive as it is external? thats what i dont get how would i safley remove the hard drive?. and 
the wallpaper for you:
[http://www.gnome-look.org/content/show.php/Ubuntu++Glass?content=31547](http://www.gnome-look.org/content/show.php/Ubuntu++Glass?content=31547)

---

### Post by Calmor on 2008-12-29
"Safely remove drive" is done in Windows.  Connect it to a computer running Windows, then in the lower right corner near the clock, there is an icon for safe removal of hardware.  Click it and choose to remove your external hard drive.  It should then work with no problem in Ubuntu.

It seems that most people have forgotten about that "safely remove hardware" icon in Windows since XP came out, as XP does not cache writes to the flash drives.  Ubuntu does cache by default, saving write cycles and providing a little better performance, but remember to unmount your external drives before removing them, or else changes may not be saved and/or data corruption can occur.

---

### Post by Big_astur on 2008-12-29
What he says it's that you boot into windows then connect the hardrive in windows and then remove it by using the green symbol which appears on your desktop, as you can see here (for windows XP or vista):
[http://kbserver.netgear.com/images/safely_remove_1.gif](http://kbserver.netgear.com/images/safely_remove_1.gif)
[http://i212.photobucket.com/albums/cc94/Dl4All/dl4all/USB-Safely-Remove.png](http://i212.photobucket.com/albums/cc94/Dl4All/dl4all/USB-Safely-Remove.png)

Now when you boot into ubuntu you won't have any problems mounting the drive.

This is what i have done when i got problems like yours. Some friends passed me hardrives which they just unplugged not in the safe way.

---

### Post by Mr N00b on 2008-12-29
> **Calmor said:**
> "Safely remove drive" is done in Windows.  Connect it to a computer running Windows, then in the lower right corner near the clock, there is an icon for safe removal of hardware.  Click it and choose to remove your external hard drive.  It should then work with no problem in Ubuntu.

It seems that most people have forgotten about that "safely remove hardware" icon in Windows since XP came out, as XP does not cache writes to the flash drives.  Ubuntu does cache by default, saving write cycles and providing a little better performance, but remember to unmount your external drives before removing them, or else changes may not be saved and/or data corruption can occur.

> **Big_astur said:**
> What he says it's that you boot into windows then connect the hardrive in windows and then remove it by using the green symbol which appears on your desktop, as you can see here (for windows XP or vista):
[http://kbserver.netgear.com/images/safely_remove_1.gif](http://kbserver.netgear.com/images/safely_remove_1.gif)
[http://i212.photobucket.com/albums/cc94/Dl4All/dl4all/USB-Safely-Remove.png](http://i212.photobucket.com/albums/cc94/Dl4All/dl4all/USB-Safely-Remove.png)

Now when you boot into ubuntu you won't have any problems mounting the drive.

This is what i have done when i got problems like yours. Some friends passed me hardrives which they just unplugged not in the safe way.

Thanks for all the help guys that was the problem now it is fixed :)

---

### Post by Abu_Dayya on 2008-12-31
Glad to know everything worked for you. I'm sorry if I wasn't very clear in my answer, but I thought most people know about the "safely remove drive" icon in windows. Thats why I put it in quotes " ". I guess now you can mark the thread as solved. You do this by clicking on the 'Thread Tools' link on the top of the page

And thank you for the wallpaper link

---

### Post by wmoore on 2008-12-31
> **Abu_Dayya said:**
> Glad to know everything worked for you. I'm sorry if I wasn't very clear in my answer, but I thought most people know about the "safely remove drive" icon in windows. Thats why I put it in quotes " ". I guess now you can mark the thread as solved. You do this by clicking on the 'Thread Tools' link on the top of the page

And thank you for the wallpaper linkI have found several IT 'professionals' who weren't aware of this feature. Not sure how that happens ...... :roll:

---

### Post by Calmor on 2009-01-02
I think everyone just got used to the fact that Windows doesn't cache the writes (at least on XP and up), so they never find any problem with just ripping out the drive.  That and Windows doesn't throw any error messages saying that it might not be a good idea... it's just an unnecessary step to most people.

The pros should know, however... that is pretty bad.

---

