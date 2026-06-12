---
title: "How to fake the pc by booting by MBR.BIN file with grub2"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by honeybear on 2010-12-11
Hello,

I have a mbr.bin that can be booted to get xp.

I have no idea how to pass it to grub with some chainloader

some experts ?? help please

I wanna play halo 3 !

---

### Post by oldfred on 2010-12-11
I have seen where users create a mbr.bin to boot grub from windows, but you should never have to do that to boot windows from grub.

If you run this does it not find your windows install?
sudo update-grub

If not post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by honeybear on 2010-12-11
> **oldfred said:**
> I have seen where users create a mbr.bin to boot grub from windows, but you should never have to do that to boot windows from grub.

If you run this does it not find your windows install?
sudo update-grub

If not post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

no way to get to run windows with a normal grub into MBR
it requires to fake it! so using mbrxp.bin for using it wiht a chainloader

---

### Post by amjjawad on 2010-12-11
> **honeybear said:**
> **no way** to get to run windows with a normal grub into MBR
**it requires to fake it**! so using mbrxp.bin for using it wiht a chainloader

Where did you learn such a great piece of information? I'm very interested to know!

I'm sorry to disappoint you and I don't mean to be "rude" at all but this is totally wrong. Sorry again :)

---

### Post by honeybear on 2010-12-12
> **amjjawad said:**
> Where did you learn such a great piece of information? I'm very interested to know!

I'm sorry to disappoint you and I don't mean to be "rude" at all but this is totally wrong. Sorry again :)

well, I know that normally it works, but I guess in this case I have windows xp in /dev/sda2 and it seems that some active /partition issues are going on because it can maybe see it as D:/

I acknowledge grub2 since it can work with almost anything. well dd restoring the xp mbr works, but grub2 fails, I tried several any possible thing to pass into cmd of grub2 but it fails

---

### Post by amjjawad on 2010-12-12
> **honeybear said:**
> well, I know that normally it works, but I guess in this case I have windows xp in /dev/sda2 and it seems that some active /partition issues are going on because it can maybe see it as D:/

I acknowledge grub2 since it can work with almost anything. well dd restoring the xp mbr works, but grub2 fails, I tried several any possible thing to pass into cmd of grub2 but it fails

Honestly, I didn't understand what you just wrote.
If you're having problems with booting, then you got generally two cases:
Either to restore MBR using fixmbr and fixboot (Windows XP CD)
Or[ re-install GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").

These are the general solutions for booting issues. Users ended up by trying one of these or perhaps both.

If you're seeking for help, please use [this]("http://bootinfoscript.sourceforge.net/"), post the result here and wrap up the text with "CODE" tags or "#". Instructions are included in the [link]("http://bootinfoscript.sourceforge.net/"). As Oldfred already suggested.

Many users here will help you to fix your problem whatever it's.

---

### Post by Rubi1200 on 2010-12-12
I suggest you post the results of the boot info script as oldfred already asked.

Without it, we are just guessing as to the actual setup and how best to advise you.

Thanks.

---

