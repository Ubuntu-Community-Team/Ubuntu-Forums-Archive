---
title: "Computer locks up after awhile of no use."
date: 2010-05-22
forum: New to Ubuntu
---

### Post by furialis on 2010-05-22
I think this may be related to my use of a SSD. After the computer has been idle for a while (or very rarely randomly when I'm using it) the screen goes blank and doesn't respond to anything and needs to be reset.

I'm using 10.04 with ext4.

---

### Post by r-senior on 2010-05-22
Do you know what your graphics chip is? What's the output of this command in a terminal?

$ lspci -nn | grep VGA

If it's Intel 8xx or maybe 9xx series, have a look at this. I'm still trying to find the permutation that works on my laptop ...

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by furialis on 2010-05-22
```

c@c:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
c@c:~$ 

```

When the computer boots, it boots fast but goes to my wallpaper with no tool bar or anything on the screen. It takes a few seconds for the icons and things to appear. Does that lend any clues?

---

### Post by r-senior on 2010-05-22
Not the Intel graphics problem then ...

Not sure I can be much help other than to say it sounds like gnome-panel isn't starting properly. If you have desktop icons that would indicate that Nautilus (file manager) is starting OK.

You could try hitting Ctrl-Alt-T, which might give you a terminal window, and then look into the log files under /var/log - messages, syslog and Xorg*.log? Alternatively Ctrl-Alt-F1 should take you to a console to do the same investigation. (Ctrl-Alt-F7 to get back to X).

Someone else might have better ideas. Have you searched for issues with your graphics chip?

---

### Post by gordintoronto on 2010-05-22
Have a look at Preferences/Screensaver.

---

### Post by rp3 on 2010-05-22
> **furialis said:**
> ```

c@c:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
c@c:~$ 

```

When the computer boots, it boots fast but goes to my wallpaper with no tool bar or anything on the screen. It takes a few seconds for the icons and things to appear. Does that lend any clues?

I think thats normal now, seeing how the OS boots so fast, and you with a SSD drive, so I don't think that means much.  As long as it gets through the  full boot of course..

I am getting ready to build a PC based a boot drive with a SSD device, just found a 32gig for 69 bux so I picked it up...

How much faster it is when booting?

---

