---
title: "Please help me :("
date: 2009-02-02
forum: New to Ubuntu
---

### Post by rjg117 on 2009-02-02
Hi, I'm having some problems. I've never used Ubuntu before, and I've never really used a forum before. I'm sorry if this question has already been asked or something.

Basically what happened was, I was running Ubuntu hardy herron (I think) and I tried updating to the latest release (Intrepid Ibex), so basically, I waited for an hour while it was updating, and then the computer restarts, I choose Ubunbu from the dual boot options, as usual. Except this time it doesnt work :( The ubuntu logo comes up, and is loading, but then instead of going to the login screen, it goes onto this black screen with white writing. It says 

"Booting 'ubuntu 8.10, kernel 2.6.27-11-generic'"

Underneath this it has my filesystem type and some other stuff. Then it says 

"loading please wait...

Ubuntu 8.10 myusername-desktop tty1"

It then asks me to login. I do so, and it then comes up with more writing, system information, and then it says there is 1 zombie process running

"Graph and manage this system at https://landscake.canonical.com/"

Then has: "myusername@myusername-desktop:~$" 

I have no idea what to do. I'm sure you can tell just by reading this I'm not great with computers.. Please help me :(

---

### Post by tangibleorange on 2009-02-02
> **rjg117 said:**
> Hi, I'm having some problems. I've never used Ubuntu before, and I've never really used a forum before. I'm sorry if this question has already been asked or something.

Basically what happened was, I was running Ubuntu hardy herron (I think) and I tried updating to the latest release (Intrepid Ibex), so basically, I waited for an hour while it was updating, and then the computer restarts, I choose Ubunbu from the dual boot options, as usual. Except this time it doesnt work :( The ubuntu logo comes up, and is loading, but then instead of going to the login screen, it goes onto this black screen with white writing. It says 

"Booting 'ubuntu 8.10, kernel 2.6.27-11-generic'"

Underneath this it has my filesystem type and some other stuff. Then it says 

"loading please wait...

Ubuntu 8.10 myusername-desktop tty1"

It then asks me to login. I do so, and it then comes up with more writing, system information, and then it says there is 1 zombie process running

"Graph and manage this system at https://landscake.canonical.com/"

Then has: "myusername@myusername-desktop:~$" 

I have no idea what to do. I'm sure you can tell just by reading this I'm not great with computers.. Please help me :(

what happens if you type

```
startx
```

at the prompt (username@hostname)

---

### Post by taurus on 2009-02-02
What happens if you run this command at the prompt?

```
startx
```

---

### Post by rjg117 on 2009-02-02
When I type: "startx" it comes up with all this writing, and then says: "Fatal server error:
No screens found
giving up
xinit: Connection refused (errno 111): Unable to connect to X server
xinit: No such  process (errno 3): Server error.
myusername@myusername-desktop:~$"

---

### Post by taurus on 2009-02-02
Try

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by rjg117 on 2009-02-02
I typed: sudo dpkg-reconfigure xserver-xorg
and hit enter, and it asked for my password. I entered it, and it comes up with this blue screen with writing. At the end it says: "Use kernel framebuffer device interface?" I need to select yes or no.

---

### Post by taurus on 2009-02-02
Pick yes first and see if X server works.  If not, run that command again from a prompt but pick no this time.

---

### Post by rjg117 on 2009-02-02
ok so I tried both yes and no. Both options take me to some thing setting up the keyboard. I just went with all the default settings, and in the end it comes up with this:

xserver-xorg postinst warning: overwriting possibly-customised configureation
   file; backup in /etc/x11/xorg.conf.20090203001610
myusername@myusername-desktop:~$

This is written in a small black part of the screen underneath a blue screen which still has the keyboard options displayed.

---

### Post by Praxicoide on 2009-02-02
Did you try typing startx again?

---

### Post by rjg117 on 2009-02-02
I tried just now, it comes up with heaps of writing, exactly the same as before.

Re: Please help me :(
When I type: "startx" it comes up with all this writing, and then says: "Fatal server error:
No screens found
giving up
xinit: Connection refused (errno 111): Unable to connect to X server
xinit: No such process (errno 3): Server error.
myusername@myusername-desktop:~$"

---

### Post by stalkingwolf on 2009-02-02
try this,
reboot. as soon as the grub menu comes up ( starting Grub ***), hit escape.
this will bring up the full boot menu.

Select the recovery entry using your down arrow.  hit enter.  It will run
the recovery then a box will pop up.  select "fix broken packages". enter.
when it finishes ( it will tell you finished) hit enter then return to boot.

If that doesnt work, reboot run the recovery and when the box comes up 
select fix X.

If that doesnt work try this command,  ```
sudo displayconfig-gtk
```

---

### Post by Neural oD on 2009-02-02
maybe there is a problem picking up your hardware - type in: sudo lshw -c display

this will show what display hardware is seen by the system.

---

### Post by rjg117 on 2009-02-02
ok so I tried recovery mode, Both things stalkingwolf sugested, and neither worked. I then tried to use the code, but it said command not found :(

I then typed the code to show the displays, and it came up with both my video cards. And then back to myusername@myusername-desktop:~$

:( Thanks for your help guys, its much appreciated. I just hope this can be fixed :( The alternative is going back to windows and formatting my Ubuntu harddrive, and just using windows. But I really want to try Ubuntu out as my main operating system...if it would work! :(

---

### Post by taurus on 2009-02-02
You have two video cards on your machine?  Which card does your monitor connect it to?

Post the output of this command from a prompt.

```
lspci | grep VGA
```

---

### Post by rjg117 on 2009-02-02
01:00.0 VGA compatible controller: nVidia corporation GeForce 8600 GT (rev a1)
02:00.0 VGA compatible controller: nVidia corporation GeForce 8600 GT (rev a1)

---

### Post by taurus on 2009-02-02
So you have two identical nvidia graphic cards.  Which card does your monitor connect to?  Perhaps you should remove one from your machine and see if X server is working/running again.

---

### Post by rjg117 on 2009-02-02
Uh I'm not really sure how.. :( I was hoping this was just a software problem... Considering Ubuntu was running fine untill I tried to update. The monitor connects to the video card on the top? Sorry :( I'm not that great with computers :(

---

### Post by Malalo on 2009-02-02
> **rjg117 said:**
> 01:00.0 VGA compatible controller: nVidia corporation GeForce 8600 GT (rev a1)
02:00.0 VGA compatible controller: nVidia corporation GeForce 8600 GT (rev a1)

Wouldn't this simply indicate that his video adapter has two outputs ?

---

### Post by taurus on 2009-02-02
Did you purchase the machine (brand/model) or did somebody built it for you?

Post the output of this command.

```
cat /etc/X11/xorg.conf
```

---

### Post by taurus on 2009-02-02
> **Malalo said:**
> Wouldn't this simply indicate that his video adapter has two outputs ?

Yes, for dualhead.

---

### Post by hajbal92 on 2009-02-02
I have also a question. My system is works fine except one thing. I have ubuntu 8.04. The app, wich shows the HDD (I dont know its name because i hava a hungarian ubuntu). Its name can be disk usage checker... IDK.
So this tool sees exactly the double sizes of the partitions. I just dont know how could I fix it. 

Ps. sorry for my english #-o

---

### Post by rjg117 on 2009-02-02
The computer was built for me.

This is what happened when I typed the above code:

section "Device"
        Identifier     "Configured Video Device"
endsection

section "Monitor"
        Identifier     "Configured Monitor"
EndSection

Section "Screen"
        Indentifier    "Default Screen"
        monitor        "Convfigured Monitor"
        Device         "Configured Video Device"
EndSection

---

### Post by Neural oD on 2009-02-02
hajbal92 - create a new thread  - by hijacking this thread not many will see your post.

---

### Post by taurus on 2009-02-02
Will see if this works?

```
sudo dpkg-reconfigure **-phigh** xserver-xorg
startx
```

---

### Post by rjg117 on 2009-02-02
When I use that code it says:

xserver-xorg postinst warning: overwriting possibly-customised configureation
     file; backup in /etc/X11/xorg.conf.20090203011603


Also, just a question, when you wrote the code, and then underneath another one:

"sudo dpkg-reconfigure -phigh xserver-xorg
startx"

Am I supposed to just add startx at the end? or do I press enter, and then type startx? Or is there some other way? Sorry, like I said, I'm kindof dumb when it comes to these things.

---

### Post by Dougie187 on 2009-02-02
Startx is a seperate command.

So, press enter and then type in startx

---

### Post by rjg117 on 2009-02-02
ok thanks, tried that, and it went right back to the start, with the "Fatal server error: no screens found
giving up

etc.etc. Its the same as written in previous posts.

---

### Post by perlluver on 2009-02-02
> **rjg117 said:**
> ok thanks, tried that, and it went right back to the start, with the "Fatal server error: no screens found
giving up

etc.etc. Its the same as written in previous posts.

Could you reboot, hit Esc. on the grub boot loader, then load up xfix.  That should take care of the xserver problem.

---

### Post by rjg117 on 2009-02-02
Already tried that, it runs, then I go boot normally, and it asks for my username and password, I enter them, and then its back to:

myusername@myusername-desktop:~$

---

### Post by rajeev1204 on 2009-02-02
What if he is using two video cards in SLI mode?

---

### Post by rjg117 on 2009-02-02
Guys I'm sorry, but I live in Australia, and its almost 2 in the morning here. So I will check this thread tomorow sometime, if anyone comes up with anything else. Thanks for all your help so far, I really appreciate it.

---

### Post by rjg117 on 2009-02-02
Ok I think I fixed it. I removed my second video card, and Ubuntu seemed to work fine :/ I guess my video card is screwed then :( Anyway thanks for all the help :) I'm glad its working now.

---

### Post by gsocker on 2009-02-02
Since it worked fine until the upgrade, the card is probably fine. Are you using SLI or dual head? If dual head, the server may need to be told explicitly which card drives which display. Not sure how SLI handles this, but you may have to specifiy which card the display is connected to.
Try reinserting the second card. Assuming startx still fails, please post the contents of "/var/log/Xorg.0.log" so people can see try and figure out why the server is giving up.

This may be helpful:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Ignore the "Starting a Terminal" section, as you already have a terminal when you see the shell prompt "[mylogin@mylogin-desktop]$

---

