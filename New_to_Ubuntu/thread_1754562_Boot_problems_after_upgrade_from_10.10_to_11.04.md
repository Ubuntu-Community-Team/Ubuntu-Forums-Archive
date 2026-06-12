---
title: "Boot problems after upgrade from 10.10 to 11.04"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by AnthonyT1967 on 2011-05-10
Please Someone help. I am totally new here and have browsed a few messages but nothing is helping me. I am not new to Ubuntu, but have been using it on and off. I use it like Microsoft windows ( Sorry to Swear lol).
I don't know anything technical about Ubuntu. The problem is - 
I was running 10.10 on my PC and have not used it for around a month as I mainly use my laptop. Now I went on it last night and everything was fine when I booted and a box came up saying that there are upgrades and an update to 11.04. So I let it do it's job. 
I later came back to it and it asked to reboot to finish updating.Again I left it for a while and when I came back to it again, it was hung on a blank screen. Anyway I tried rebooting it, but it just goes to what I call a doss screen - command line, asking me to enter my user name and password so I enter it and not a lot happens. Why has this happened, any Ideas? I can get to a recovery list and tried recovering Grub bootloader ( I think )and I have done a file system check with nothing found. 
Please - Anybody got any Ideas

Cheers

---

### Post by sikander3786 on 2011-05-10
Welcome to the forums :-)

This is surely not a bootloader problem at all as your PC is booting successfully to the command line. The only thing wrong is with your graphics settings so lets tweak it.

Backup your xorg.conf file and create a new one. xorg.conf handles the graphics properties etc.

Login to the command line using your username/password and execute these commands one by one.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note, capital 'X' for X11. It is case sensitive.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

So, we'll see the results after the reboot :-)

And mind you, the new version of Ubuntu 11.04 comes with Unity, a new desktop interface (which is not perfectly perfect yet) so we might need to work a bit more to get everything up and running.

---

### Post by AnthonyT1967 on 2011-05-10
WOW Thanks - That was quick - Just went on the drums for 10 mins thinking nobody would answer so quickly.

Thank You, I will print what you have put and give it a try, but bare with me.It may take me a while lol

Tony

---

### Post by AnthonyT1967 on 2011-05-10
Thank you for that and it loaded to login screen.
I put password and a box appears saying - 
"It seems that you do not have the hardware required to run Unity, please choose Ubuntu Classic at the Login Screen and you will be using the traditional environment".

I Clicked close  and main window with different wallpaper loaded with all my original icons.

I have not rebooted yet - not until you instruct me to.

I have half a smile on my face now lol.

Thanks - Tony

---

### Post by sikander3786 on 2011-05-10
Glad you got it that far :-)

Can you see the login screen? If yes, click your username and session option should appear in the bottom of your screen. Choose 'Ubuntu Classic', put in your password and login. This should take you to the regular Gnome Desktop. Here, launch the Terminal by pressing Ctrl + Alt + T or going to Applications > Accessories > Terminal and post the output of following command so we can see if you'll be able to run Unity or not.

```
/usr/lib/nux/unity_support_test -p
```

Only if the above method doesn't work:

If you can't see the login screen as you have already tried to login, press Ctrl + Alt + F1 no matter what ever is there on your screen. tty (Terminal) should appear. Type,

```
sudo service gdm stop
```

```
sudo service gdm start
```

Login to 'Ubuntu Classic' and follow the steps above.

If none of the above works, reboot your PC and follow the same procedure for getting to the desktop.

---

### Post by AnthonyT1967 on 2011-05-10
I will have to reboot again or can I just log out?

---

### Post by sikander3786 on 2011-05-10
> **AnthonyT1967 said:**
> I will have to reboot again or can I just log out?
If possible, logout and try the 'Ubuntu Classic' session from Login Screen. If unable to logout, restart gdm or if that doesn't work either, reboot is the only choice :-)

---

### Post by AnthonyT1967 on 2011-05-10
Right i did as you said and wasn't sure what has happened - not a lot it went back into it and has loaded what appears to be the same screen and wallpaper of space cartoon in blue.
So I think I've done right.

---

### Post by sikander3786 on 2011-05-10
> **AnthonyT1967 said:**
> Right i did as you said and wasn't sure what has happened - not a lot it went back into it and has loaded what appears to be the same screen and wallpaper of space cartoon in blue.
So I think I've done right.
You mean it took you back to the Login Screen? Can't you see the desktop, panels. icons etc? Were you able to choose 'Ubuntu Classic'?

---

### Post by AnthonyT1967 on 2011-05-10
Yes I chose Ubuntu classic and it loaded and went into the screen. Does that mean you have fixed it for me? or is there something else I need to do.

---

### Post by sikander3786 on 2011-05-10
By screen, you mean the desktop is ok and usable? If yes, we might not need to do anything else unless you want to run Unity, the new Ubuntu DE based on Gnome initially. If you want to run it, we need to see the output of this command from Terminal.

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by AnthonyT1967 on 2011-05-10
So sorry for not replying - I didn't see that there was a second page lol.
 Would be nice to run it as Unity, but if it's not very stable then would rather stick to my current Gnome. What do you think. 
I am getting a new hard drive soon and will probably put the latest reincarnation on it. My daughter keeps asking for an apple mac - So Ubuntu is the closest thing I think of and is FREE.
Anyway thank you for your time and the speed that you answered to my shout for help.
Thanks - Tony

---

### Post by sikander3786 on 2011-05-10
For running Unity, we need to see the output of command mentioned in my last post.

Unity is worth tring in my opinion. New Launcher, dash, panels, way of behaviour and what not.

If you don't want to test it, you've at least got a working system :-)

Good Luck!

---

### Post by sikander3786 on 2011-05-10
For running Unity, we need to see the output of command mentioned in my last post.

Unity is worth tring in my opinion. New Launcher, dash, panels, way of behaviour and what not.

If you don't want to test it, you've at least got a working system :-)

Good Luck!

---

### Post by AnthonyT1967 on 2011-05-10
Im sorry if i'm taking a long time to reply - I have my daughter now, so can only do it as and when now. I will try what you said in your last post - 

Thanks

---

