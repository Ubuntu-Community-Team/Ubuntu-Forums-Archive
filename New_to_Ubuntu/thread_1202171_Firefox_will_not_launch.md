---
title: "Firefox will not launch"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Zync on 2009-07-01
Hello,  I just loaded ubuntu 9.04 on my Acer Aspire 3690 using the dual boot option with Windows Vista Home Basic being previously installed.  Everything appeared to be going well, but after rebooting the system, Firefox would not launch from ubuntu.  I also have Firefox loaded on the windows version.  I am wondering if it may be looking at the windows version rather than the ubuntu version.  Any ideas would be appeciated.  Thanks

Zync

---

### Post by Geoff918 on 2009-07-01
Well, it's definitely not looking at the windows version (unless you're going through the file manager to locate that version). How are you attempting to launch the program?

---

### Post by ~sHyLoCk~ on 2009-07-01
> **Zync said:**
> Hello,  I just loaded ubuntu 9.04 on my Acer Aspire 3690 using the dual boot option with Windows Vista Home Basic being previously installed.  Everything appeared to be going well, but after rebooting the system, Firefox would not launch from ubuntu.  I also have Firefox loaded on the windows version.  I am wondering if it may be looking at the windows version rather than the ubuntu version.  Any ideas would be appeciated.  Thanks

Zync

No it has no link with the Windows version, go to > Applications->Accessories->Terminal
and type ```
firefox
```

And see if it launches, if it doesn't paste the output here!

---

### Post by Zync on 2009-07-02
> **Geoff918 said:**
> Well, it's definitely not looking at the windows version (unless you're going through the file manager to locate that version). How are you attempting to launch the program?
I am clicking the icon from the "Applications" menu in Ubuntu.  a message appears at the bottom of the screen saying it is starting Firefox, but it never opens.  I think I will download Firefox 3.5 from the Mozilla site and try it.  I agree that it couldn't be looking at the Windows version, it's just strange that it would not open the program.  Oddly, it does not so an error or crash report either.  Thanks for your reply.

Zync

---

### Post by lovinglinux on 2009-07-02
> **Zync said:**
> I am clicking the icon from the "Applications" menu in Ubuntu.  a message appears at the bottom of the screen saying it is starting Firefox, but it never opens.  I think I will download Firefox 3.5 from the Mozilla site and try it.  I agree that it couldn't be looking at the Windows version, it's just strange that it would not open the program.  Oddly, it does not so an error or crash report either.  Thanks for your reply.

Zync

It could be a corrupted profile. Move the contents of ~/.mozilla/firefox/ to somewhere else and start Firefox.

---

### Post by Zync on 2009-07-02
> **lovinglinux said:**
> It could be a corrupted profile. Move the contents of ~/.mozilla/firefox/ to somewhere else and start Firefox.
It was a corrupted profile.  I did what you suggested and it worked great.  I'm scratchin my head as to why it was corrupted though.  I guess it rains huh???  Thanks Again.

Zync

---

### Post by lovinglinux on 2009-07-03
> **Zync said:**
> It was a corrupted profile.  I did what you suggested and it worked great.  I'm scratchin my head as to why it was corrupted though.  I guess it rains huh???  Thanks Again.

Zync

Corrupted profiles are actually a very common thing. That's why I recommend reading the **Backup** section of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Usually there is no need to delete the entire profile, just the file that is corrupted. But it is easier to delete the entire thing instead of trying to find the culprit. If you see strange things happening on Firefox, like bookmarks missing, settings reverting to default and toolbars not working, visit the troubleshooting section of that thread. I'm constantly updating it with new problems and solutions.

---

