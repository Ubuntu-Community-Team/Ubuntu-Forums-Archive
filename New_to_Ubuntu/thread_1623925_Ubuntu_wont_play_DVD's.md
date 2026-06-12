---
title: "Ubuntu wont play DVD's"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Zundap on 2010-11-17
[SIZE=2][COLOR=#000000]Hi, could one please help, I have just tried to play a DVD in ubuntu 10.10, but it wont play, the i message i got was as below.
[/COLOR][/SIZE]

> 
[SIZE=2][COLOR=#ff0000]Your input can't be opened:[/COLOR][/SIZE]
 [SIZE=2][COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]

[/COLOR][/SIZE][SIZE=2][COLOR=#000000]I have followed advice in another thread with the same error message, the advice was to run[/COLOR][/SIZE]> [COLOR=#000000] **&#8220;**[/COLOR]**sudo apt-get install totem-xine libxine1-ffmpeg in terminal**&#8221;[SIZE=2] that did not cure the problem, the next suggestion was to type this command in to terminal - [/SIZE]> **sudo apt-get install vlc ** 
[SIZE=2]This has not worked either, could anyone tell me how to cure this problem, thanks. [/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE]

---

### Post by yetiman64 on 2010-11-17
If you have not already installed libdvdcss2 yourself, then in terminal run,
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```when then terminal completes the install try opening a dvd in vlc again.

This is one possible problem but without the vlc log error I'm not sure if this actually is your problem, but is worth a try. 

In vlc to view the log for a specific error go to the tools menu > messages.

---

### Post by philinux on 2010-11-17
> **Zundap said:**
> [SIZE=2][COLOR=#000000]Hi, could one please help, I have just tried to play a DVD in ubuntu 10.10, but it wont play, the i message i got was as below.
[/COLOR][/SIZE]

[SIZE=2][COLOR=#000000]

[/COLOR][/SIZE][SIZE=2][COLOR=#000000]I have followed advice in another thread with the same error message, the advice was to run[/COLOR][/SIZE][SIZE=2] that did not cure the problem, the next suggestion was to type this command in to terminal - [/SIZE]
[SIZE=2]This has not worked either, could anyone tell me how to cure this problem, thanks. [/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE]

You need the medibuntu repos.

[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

---

### Post by linuxforartists on 2010-11-17
This is a common problem for beginners.  The other posters covered this pretty well.

If you're still confused, here's a video tutorial that helped me a lot:
[URL="http://www.youtube.com/watch?v=NT7urt5UcQg"]
Ubuntu Linux Tutorial - Multimedia, Codecs, Medibuntu![/URL]

Also helps that the host is a lovely gal :P

---

### Post by Zundap on 2010-11-17
p { margin-bottom: 0.21cm; }  Thanks everyone for you prompt replies, I ran the code that yetiman64 provided, started VLC and opened the video through it and it is now playing the DVD, both picture and sound perfectly.
 

 Thanks again to all of you, i am most grateful, cheers Zundap.   :)

---

