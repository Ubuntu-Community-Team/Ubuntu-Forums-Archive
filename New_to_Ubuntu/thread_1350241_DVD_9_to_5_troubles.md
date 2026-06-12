---
title: "DVD 9 to 5 troubles"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by al.adab on 2009-12-09
hello,
is anyone using DVD 9 to 5? It's driving me insane (and looking for an alternative - not K9copy, as it crashes on start-up): 

I insert the DVD, change the DVD and ISO file space in Properties (otherwise the new folder created after burning the dvd it ends up deep inside File system, in TXT, for some reason), and select Desktop and Video as destinations...

...and when the application is about to finish burning the DVD onto my HD, it asks me if I want to play it (?). Two arrows, back and forward, also appear. No matter what I chose, the computer ejects the DVD shortly after this, and the folder that was being created on my desktop disappears!

Do you know what the matter is?

---

### Post by indytim on 2009-12-09
I don't know anything about your app.  Here's a far off suggestion though... Make sure you're trying to write to an ext3 partition with enough free space.  If you're trying to dump the iso to FAT32... won't work due to size restrictions on FAT32.

Hope this snippet helps.

IndyTim

---

### Post by SteveNorman on 2009-12-09
what type of dvd's? if your talking about backing up your legally obtained movies you can use vobcopy. A superior ripping tool.


[http://www.toastboy.com/main/unixlinux/using-vobcopy-and-mkisofs-to-backup-dvds-to-harddrive/](http://www.toastboy.com/main/unixlinux/using-vobcopy-and-mkisofs-to-backup-dvds-to-harddrive/)

---

### Post by al.adab on 2009-12-09
any kind of DVD...occasionally I rent a DVD and if I liked it I'd like to copy it on my HD. This is probably illegal, I know...

---

### Post by SteveNorman on 2009-12-09
oh its very illegal. So dont use vobcopy to do that. Only use it on ones you purchased for the sole purpose of legal backups. Otherwise the interpol will drop what they are doing and rush over and knock stuff down.

But for your legally owned dvds vobcopy plus the appropriate libraries listed in my link will do the trick.

Playback is better with VLC imho

---

### Post by al.adab on 2009-12-09
Got it. I've tried out Vobcopy on one of my legally-owned DVDs and it worked perfectly. Thanks!

---

### Post by Hallvor on 2009-12-09
> **al.adab said:**
> any kind of DVD...occasionally I rent a DVD and if I liked it I'd like to copy it on my HD. This is probably illegal, I know...

It depends on Egyptian law, and I am certainly not an expert. But assuming it is legal: There is an application called DVDFab decrypter that should do the trick. It is made for Windows, but runs in Wine. It will copy DVDs even if they are copy protected. It is very easy to use and has a lot of nice features. I haven`t had as much luck with native applications.

---

### Post by al.adab on 2009-12-09
Thanks Hallvor. Egyptian copyright law is not well-defined as far as I know, need to look into it. I suppose international copyright law applies to some extent anyway. Thanks for the tips.

---

### Post by SteveNorman on 2009-12-09
Its also an issue of forum rules, we cant really help anyone do that sort of thing so the wording has to be proper ;)

---

