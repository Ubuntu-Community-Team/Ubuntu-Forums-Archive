---
title: "background audio cannot shutdown"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by senorian on 2011-08-06
my grand son was playing games on PBS kids.
When he quit there was still an audio signal saying:
explorer, she needs help
you are doing great explorer
move the mouse around the room
see if you can find any wood thing

I closed all windows and just had the desk top.
I shut down the computer and then restarted it many times
Always the voice saying those words came back
I tried the cli "jobs -l" but there was no response
htop did not indicate which process was causing the problem

ubuntu 10.04
athlon 11 x4 640
asus gts450
asus m4A88TD-VEV0/usb3 motherboard
memory  4 gig
Thanks 
(if there is a book which covers this please let me know)

---

### Post by cdavid13 on 2011-08-06
That is interesting I have had a problem similar but a restart  fixed the issue you got a tough one there. Have you tried going back to the site and exit out again then restart?

---

### Post by maxar6 on 2011-08-06
I have had a problem like this open up system moniter and either look for something about your browser or sound and then once you find it click end process. If that does not fix it i do not know what your problem is. It could be a virus for ubuntu rare but possible.

---

### Post by lmarmisa on 2011-08-06
Take a look to Startup Applications (System -> Preferences -> Startup Applications) and check if you find something suspicious.

I suppose the problem is limited to your user account. You could create a new user account (for example, test) for checking it.

---

### Post by senorian on 2011-08-06
Thanks
I went back to PBS kids; but I don't know which games/videos he was playing.
Leaving the website still did not eliminate the audio

---

### Post by maxar6 on 2011-08-06
What browser are you using?

---

### Post by senorian on 2011-08-06
Thanks
I created a test account and the audio was GONE
I would like to move my bookmarks to this account
if you could point me to info on how to do this
thanks

ps I would still like to know how to identify and kill the process that leaves the audio running/

---

### Post by maxar6 on 2011-08-06
again what browser are you using so you can transfer your bookmarks.

---

### Post by cdavid13 on 2011-08-06
Have you tried opening up the system monitor and checking to see if one of the processes is running that shouldn't be or one that looks out of the ordinary?

---

### Post by lmarmisa on 2011-08-06
Open Firefox and select Bookmarks -> Organize Bookmarks -> Import & Backup -> Export HTML. Save the file bookmarks.html in your home folder.

If you wish to import the bookmarks, open Firegox running inside your test account and select Bookmarks -> Organize Bookmarks -> Import & Backup -> Import HTML. The file to import will be located at /home/youruser1/bookmarks.html.

An important question. Do you hear those voices while you run Firefox or just after the login?.

---

### Post by maxar6 on 2011-08-06
Do you know if the game he was playing using flash?

---

### Post by senorian on 2011-08-06
Thanks to all for your help
firefox 3.6.18

I hear it both when logged in and when I launck Firefox

Thanks lmarmisa  for the info re bookmarks

---

### Post by lmarmisa on 2011-08-06
Have you seen something strange in System -> Preferences -> Startup Applications?.

---

### Post by senorian on 2011-08-07
lmarmisa
No but I don't know enough to know what might be strange
The trouble (for me) about htop and top is that I don't know the relationship between the pid number and the process that I would need to kill;
According to one source the command "jobs" should tell me; but I get no reponse and synaptic does not list "jobs"
If you can refer me to a site which is both newbie friendly (i.e this more or less rules out "man" pages) and shows me how to get this info I would be VERY happy
Thanks

---

### Post by lmarmisa on 2011-08-07
This command will show you if some programs were added to the startup applications of your user account. Open a terminal and type the command:

```

ls -l /home/youruser1/.config/autostart/

```

Try to post the result here if the folder is not empty.

---

### Post by senorian on 2011-08-07
jan@jan-desktop:~$ ls -l /home/jan/.config/autostart/
total 8
-rw-r--r-- 1 jan jan 352 2010-12-15 22:08 evolution-alarm-notify.desktop
-rw-r--r-- 1 jan jan 354 2011-01-09 17:45 libcanberra-login-sound.desktop
jan@jan-desktop:~$ 

Hope this helps
It seems that I have lost the panel( or one of the panels)that are on the lower edge of the screen.
At least there is such a panel, on my xubuntu old comp,which shows what window i have minimised .Does this make sense?
Thanks lmarmisa

---

### Post by lmarmisa on 2011-08-07
> **senorian said:**
> jan@jan-desktop:~$ ls -l /home/jan/.config/autostart/
total 8
-rw-r--r-- 1 jan jan 352 2010-12-15 22:08 evolution-alarm-notify.desktop
-rw-r--r-- 1 jan jan 354 2011-01-09 17:45 libcanberra-login-sound.desktop
jan@jan-desktop:~$ 

Hope this helps
It seems that I have lost the panel( or one of the panels)that are on the lower edge of the screen.
At least there is such a panel, on my xubuntu old comp,which shows what window i have minimised .Does this make sense?
Thanks lmarmisa

Your sound problem could be related to **libcanberra-login-sound.desktop**.

Please, post the result of this command:

```

cat /home/jan/.config/autostart/libcanberra-login-sound.desktop

```

How recent is your second problem (the lost panel)?.

---

### Post by senorian on 2011-08-08
lmarmisa

jan@jan-desktop:~$ cat /home/jan/.config/autostart/libcanberra-login-sound.desktop

[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/sound/event_sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound
X-GNOME-Autostart-enabled=false
jan@jan-desktop:~$ 

Acouple of months
I am unable to import my bookmarks from /home/jan/ to the "test" user account. The wizard seems unable to do anything
There is a new 10.04.3 iso available and I am thinking that that may be the simplest solution
Thanks for you help

---

### Post by lmarmisa on 2011-08-09
If you have problems importing you bookmark from **/home/jan** try this command (login to test):

```

cp /home/jan/bookmarks.html ~

```

Then open Firefox and import the bookmarks from your home directory.

In relation with the weird sound, I recommend to type these commands (login to jan):

```

rm ~/.config/autostart/libcanberra-login-sound.desktop
rm -r ~/.adobe
rm -r ~/.pulse*

```

Reboot and check if the problem is solved.

---

### Post by senorian on 2011-08-10
lmarmisa
The bookmarks still refuse to be imported to "test" user/

Your instructions as to how to eliminate the sound *DID NOT WORK*



(but what else does removing Adobe do?)

Unfortunately i now (this before I followed your instuctions)  find that I am unable to "save page as"

I am now going to reinstall
BUT I would really like to know how to recover my bottom panel after my grandson has been plaing games on my computer. And not just the bottom panel but any other "button" pushes he might do.
I was thinking of getting hin a cheap notebook either this xmas or the next; but if he is able to fubar it any time he uses it; and I am left with only the option of reinstalling each time I will have to think twice.Perhaps using a live cd would eliminate any possibility of fubar?
This is off topic but if you have any thoughts on this apparent problem I would be grateful

---

