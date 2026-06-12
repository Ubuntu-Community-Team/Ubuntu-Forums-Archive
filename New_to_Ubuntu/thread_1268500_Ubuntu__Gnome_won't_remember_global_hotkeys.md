---
title: "Ubuntu / Gnome won't remember global hotkeys"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by sisosteven on 2009-09-17
Dear Uby-folks,

There is a weird problem with my global hotkeys. When I set them up (system / preverences / shortkeys), they seem to work fine. But after reboot, the media-keys don't work no more.
I am using Ubuntu 8.04 by the way. Oh, and I am from the Netherlands, so my English may be a little weird :-)
But I did not get an answere on the Dutch forum.

Thank you for your help.

Greetings,

Steven

---

### Post by Excedio on 2009-09-17
You could try to use gconf to set key-bindings...it's what I use.
```
sudo apt-get install gconf-editor
```Then go to Applications > System Tools > Configuration Editor

Expand Apps > Metacity > global_keybindings
    From here you need to type in a Value for one of the run_command_#
*Example: <Super>T*

Expand Apps > Metacity > keybinding_commands
    From here you need to type in a Value for the command_# that corresponds with the run_command_#
*Example: gnome-terminal*

This will open up the terminal for me when I press Super and T at the same time.

---

### Post by sisosteven on 2009-09-17
Excedio,
Thank you for your reply.
I tried to follow your advise. I know the gconf-editor and the options it gives in keybindings.
All the "normal" keybindings are working perfect with this tool. For instance: <Control><Alt>T opens the gnome-terminal for me. This works great. I configured some keybindings this way.

But: this method does not provide a way to use my media-keys (some special keys that should open my Internet Browser, Mail Client, Calculator, Volume up and down, Play/Pause, etcetera.

I am afraid that this method does not give me what I was looking for, unfortunately.
Thank you anyway, for thinking with me.

Greetings,

Steven

---

### Post by Excedio on 2009-09-17
Ok...I see what you mean. What kind of keyboard are you using? Sometimes there are special utility programs that will allow you to get these to work correctly.

Let me see if I can find the same program that I tried to use in the past.

---

### Post by Excedio on 2009-09-17
This thread may be helpful to you .

[http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)

---

### Post by sisosteven on 2009-09-18
Excedio,
Many thanks for thinking with me.
And for the link to this "keytouch"-application.

I have tried that app for a long time ago (with another keyboard), and it was dramatically bad back then.
But I think I will give it another shot this time.
By the way:
I am using a Logitech Media Keyboard Elite.

I will let you know how things went with the link you gave me.

Greetings,

Steven

---

### Post by sisosteven on 2009-09-18
Excedio,

The link you gave me - well that was just a pity, because I failed at step 1, where I should press my media keys in a real console. According to this How To, I should get some output, but I did not. So I was unable to find out the keycodes that way.

I installed Keytouch - which happens to be in the repositories. With that little app, I was able to set my media keys. It is still a little buggy, because one key makes my system fall asleep, unless it is the Zoom 100% key. Well I do not use that key, so I think it is allright now.

So:
This thread is nearly solved, but the rest will be up to me. I will play around with Keytouch the next couple of weeks.

Thank you for your help, my friend :)

Many greetings from The Netherlands,

Steven

---

### Post by sisosteven on 2009-09-23
OK,
I know that I have marked this thread as 'solved', but I feel I have to share the real solution.

As I said, I have a Logitech Media Elite Keyboard.
This week I found a How-To on the Internet, which helped me to finally get the mediakeys to work in Ubuntu 8.04.

The link:
[http://www.linuxinfusion.com/configuring-logitech-media-keyboard-elite-linux](http://www.linuxinfusion.com/configuring-logitech-media-keyboard-elite-linux)

The only thing that you should not do, if you use gdm to log in, is this:
> 
"Next edit your .xinitrc or .xsession file and insert xmodmap ~/.Xmodmap & towards the top of the file."


Oh ya, and when you make your ".Xmodmap", make sure that you do not put any 'comment-lines' in it (starting with #). I did that, but it caused faillure when starting X.

Hopefully this is of help to someone,

greetings,

Steven

---

