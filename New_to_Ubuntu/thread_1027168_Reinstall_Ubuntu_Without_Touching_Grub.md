---
title: "Reinstall Ubuntu Without Touching Grub"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by RealG187 on 2009-01-01
[http://ubuntuforums.org/showthread.php?t=1025831](http://ubuntuforums.org/showthread.php?t=1025831)

Because of the problems I am having I am thinking of reinstalling Ubuntu. However, I edited my grub:

> **RealG187 said:**
> In grub Windows Vista/Longhorn (Loader) is listed twice, one is the HP recovery partition. I can simply [edit grub]("http://kubuntuforums.net/forums/index.php?topic=3093372.0") to move the recovery over and make it say recovery.

and I don't want to lost the changes.


If I reinstall Ubuntu will it reset grub, or will it see Grub is already there and leave it alone?

If not, could I just backup my grub.lst file and then after I am done reinstalling restore it and "update-grub"?

---

### Post by Coder543 on 2009-01-01
When you are on the final confirmation step of the installer you will have an Advanced... button that asks whether or not to install the boot loader. That is all I can help with this subject. Also, install [kgrubeditor]("apt:kgrubeditor")










[]("apt:kgrubeditor")

---

### Post by handydan918 on 2009-01-01
Let's not confuse grub with /boot/grub/menu.list. You can copy your /boot/grub/menu.list to a flashdrive, or email it to yourself, or whatever. Then go ahead and hose what you want to, and after you boot into your new system, cpy the /boot/grub/menu.list from your back up onto your system. 

Enjoy.

---

### Post by RealG187 on 2009-01-01
> **handydan918 said:**
> cpy the /boot/grub/menu.list from your back up onto your system.
Don't I have to run update-grub after I restore it to apply it to the MBR?

---

### Post by gn2 on 2009-01-01
You can replace the contents of menu.lst without rewriting the MBR.

All the Grub info you'll ever need is in the Hermanzone link in my sig.

---

### Post by caljohnsmith on 2009-01-01
> **RealG187 said:**
> Don't I have to run update-grub after I restore it to apply it to the MBR?
Fortunately, no, you don't have to run update-grub to apply the changes to the MBR. The update-grub command can be used to create a new menu.lst or to update an all ready existing menu.lst with new kernels for example. But if you have Grub correctly installed to your MBR, Grub will read whichever menu.lst is present in Grub's directory, so there is no need to make any changes to the MBR. I would recommend following handydan918's advice and simply back up your menu.lst (like to your online email account) if you are worried your new menu.lst will have errors. One thing to be aware of though is if you reinstall Ubuntu and format its partition, it's likely that its UUID will change, and thus your saved menu.lst won't work unless you modify it. If I were in your shoes I would simply reinstall and not worry about the menu.lst; if you run into any problems with your menu.lst, post back here, and it should be a simple thing to sort out. Good luck and let us know how it goes.

---

### Post by RealG187 on 2009-01-01
I am confused, I thought "update-grub" applies the menu.list file to the drive?

So if I would backup my menu.list and restore it, how would I apply it?

---

### Post by caljohnsmith on 2009-01-01
> **RealG187 said:**
> I am confused, I thought "update-grub" applies the menu.list file to the drive?

So if I would backup my menu.list and restore it, how would I apply it?
On start up, Grub simply loads whichever menu.lst is present in your /boot/grub directory; so if you change the menu.lst, the next time you reboot you will see the changes. You don't have to notify Grub of the changes, because on start up Grub just blindly tries to load whichever menu.lst is present in /boot/grub. So if you want to restore your old menu.lst for example, simply delete or move the one that all ready exists in /boot/grub, then put your old menu.lst in the /boot/grub directory, and next time on start up you should see your old menu.lst. Is that a little less confusing or did I not explain that well?

---

### Post by adult swim on 2009-01-01
the menu.lst file is read every time grub is run.  update-grub looks in your /boot for new kernel entries and adds them to the menu.lst as needed.  if you backed up your menu.lst file and wanted to apply it to the new installation, all you would have to do is save the backup as /boot/grub/menu.lst.  as was mentioned earlier, you will probably run into problems because your uuid's may be changed.  as caljohn said, dont worry so much about the list, its not hard to get a new one working the way you want it to.

---

### Post by egalvan on 2009-01-01
> **adult swim said:**
>   as caljohn said, dont worry so much about the list, its not hard to get a new one working the way you want it to.

For the first time I am disagreeing with caljohn's advice...:confused:

Sometimes one spends a while getting the NON-LINUX stuff in menu.lst JUST RIGHT...especially when one does not have all that much practice with menu.lst....

So blindly saying "it's not hard to get it working" doesn't take into account the OP's experience level...

i would suggest he back up his menu.lst to a flash drive (safe) or the root of the windows install (if you hose windows, you have problems)

Then when you reinstall Ubuntu, upload both new and old menu.lst and the smart guys here will help you get the new menu.lst ship-shape...

Unless you can figure it out on your own...

---

### Post by adult swim on 2009-01-01
caljohnsmith (and meirva?) has that sweet new script which outputs everything youd ever want to know about mbr/boot/partition setup.  with just a couple of posts hed be up an running.

---

### Post by caljohnsmith on 2009-01-01
> **egalvan said:**
> For the first time I am disagreeing with caljohn's advice...:confused:

Sometimes one spends a while getting the NON-LINUX stuff in menu.lst JUST RIGHT...especially when one does not have all that much practice with menu.lst....

So blindly saying "it's not hard to get it working" doesn't take into account the OP's experience level...

i would suggest he back up his menu.lst to a flash drive (safe) or the root of the windows install (if you hose windows, you have problems)

Then when you reinstall Ubuntu, upload both new and old menu.lst and the smart guys here will help you get the new menu.lst ship-shape...

Unless you can figure it out on your own...
I agree with you Ernest that having a backup of the menu.lst is a really good idea, it's just that he mentioned that he is going to reinstall Ubuntu; if he does that, it is quite likely his UUIDs are going to change, and thus the old Ubuntu entries wouldn't work unless he tweaks them with the new UUID. Also his kernels could change, so bottom line I thought it would be fine to just go with a new menu.lst. Then he can copy over his Vista entries if he wants to, which I think might be a good solution. I guess it's a matter of personal preference and level of experience (as you say) as far as how one would go about it. Cheers and Happy New Year. :)

---

### Post by RealG187 on 2009-01-01
I could easily make the changes again, but it would be even easier if I didn't have to.

I was told the Grub settings are stored in the MBR and to use 'update-grub' to apply them, but if it reads the menu.list every boot, so that means I don't have to type update-grub every time I change the menu.list?

---

### Post by adult swim on 2009-01-01
you dont need to run update-grub every time you edit menu.lst

---

### Post by egalvan on 2009-01-01
> **adult swim said:**
> caljohnsmith (and meirva?) has that **sweet new script which outputs everything youd ever want to know about mbr/boot/partition setup.**  with just a couple of posts hed be up an running.

Absolutely sweet...:KS

which is why I am shamelessly using that script left and right, and making sure my *nix cohorts have a copy....

It has given me great insight into some inner workings of *nix.

And studying the script has also given me the courage to try my hand at scripting.
(my first was a desktop launcher to automatically open menu.lst in a rooted text editor....
 yeah, I know, real simple "hello-world" stuff... but it works! Or is that not considered "scripting"? I don't know.)

Gotta love that FOSS-style stuff.

Thanks, caljohn.

ErnestG

---

### Post by egalvan on 2009-01-01
> **RealG187 said:**
> I could easily make the changes again, but it would be even easier if I didn't have to.

Yeah, always easier to do it once only...

but it IS a learning experience to mess it up and have to try again...

"Why do we fall?
 To learn to get back up again"
*Batman Begins*

The Voice of Experience

> 
I was told the Grub settings are stored in the MBR and to use 'update-grub' to apply them, but if it reads the menu.list every boot, so that means I don't have to type update-grub every time I change the menu.list?

Well yes, some settings are stored in the MBR, but in this case what you need is only stored in the menu.lst...

I have been experimenting a lot with menu.lst, breaking it,  and repairing my mistaeaks...
 but I have a completely separate machine that I "play" with, so mistakes do not leave me stranded. Far easier on the nerves, too.

caljohn's postings have been quite valuble...


And a P.S.

Regarding UUID's changing....

this is why I do not use UUID's

I use LABELS instead...


Also, 

   **hh804-boot**

or

   **puppy412-boot**

is FAR more human-readable than

   **4sada54-rbbfsdvb56-asffj-blah-blah-blah **

don't you agree?

And labels stay the same unless I erase the partition.

Yes, UUID's have their place...but in my use of Linux, not for me.

---

### Post by caljohnsmith on 2009-01-01
> **egalvan said:**
> 
Regarding UUID's changing....

this is why I do not use UUID's

I use LABELS instead...

Whenever I think of UUIDs vs. labels, I can't help but think it is sort of analogous to going to the store to buy say a package of nuts; I don't ask the clerk if they sell "76538-98742" or whatever the bar code is for the package of nuts, I simply ask for a package of nuts. So I totally agree, I think labels make a lot more sense than UUIDs. :)

---

### Post by RealG187 on 2009-01-02
When you say Labels, do you mean drive labels? What exactly is a UUID?

So I backed up my menu.list and reinstalled and it worked (I think*), but instead of installed 8.10 and not 8.04)  so now the grub menu says something different.

* So I tried 8.04 live on experience ubuntu.ogg and it did it, I tried the ogv on 8.10 and it worked!! There was no sound but I don't think there's sound in it, I tried experience ubuntu.ogg (copied it over from 8.04) and it worked, now to [get my wireless working again](http://ubuntuforums.org/showthread.php?p=6460304#post6460304), install the restricted drivers and webcam software (cheese) and enjoy Ubuntu finally (it should work now, hopefully)

---

