---
title: "Start/Stop script + starter for Network"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by perixx on 2007-11-03
Good evening everyone!


I want to make a single starter on my desktop which checks wheter network is active or not and turns on/off network connection respectively. I know I need a background script for the starter, but I've got no clue on scripting... can anybody please help me out?

Thank your!


perixx

---

### Post by kevdog on 2007-11-03
Do you really need a script for this, or would something like wicd which automatically reconnects if the network connection is dropped be adequate?

---

### Post by walkerk on 2007-11-03
easy enough but i too recommend [wicd]("http://wicd.sourceforge.net")

---

### Post by perixx on 2007-11-04
Well, I just want to keep the system as lean as possible and have no need for wireless con's / encryption etc.

Is your suggested proggy configurable in terms of setting the time for automatic connection disruption and does it notice internet access by Firefox / Thunderbird, thus auto-connecting e.g.? 

Basically, I only want to have to have some Symlink to a small script that automatically switches between "pon dsl-provider" / "poff dsl-provider", similar to "if - then" query, as needed.

Perhaps you could kindly provide some example code for me?


thx, 
perixx

---

### Post by kevdog on 2007-11-04
No the program will not do this.  That all would have to be done through a program/script.  Some of the things you want would demand a very involved program.  I dont think I would be the one to reliably give you all the script code to do what you want.  A python program may be more what you want that runs as a daemon in the background -- not a simple script file.

---

### Post by perixx on 2007-11-04
Sure, a python script would be fine - if you can provide one; I've got no clue on how to script! 

As I said, a simple switch-script would do for nox.


perixx

---

### Post by kevdog on 2007-11-04
Sorry I cant provide you with one.  I dont think you quite grasp the complexity of what you want!!

---

### Post by perixx on 2007-11-04
well, perhaps :)


I suppose it would be sth. like (in spoken words):

- check if network already running 
- if outcome is yes, then do 'poff ...'
- if outcome is no, then do 'pon...' 

perixx

---

### Post by perixx on 2007-11-04
Is there still hope for a sample-script for a pon/poff starter-switch? 

|:{/


perixx

---

### Post by robert_pectol on 2007-11-04
> **perixx said:**
> well, perhaps :)


I suppose it would be sth. like (in spoken words):

- check if network already running 
- if outcome is yes, then do 'poff ...'
- if outcome is no, then do 'pon...' 

perixx

Sounds simple enough.  Here's some sample code to help you get started:

```

#!/bin/bash
#
#  starts/stops ppp connection based on
#  detected previous state
#
##############################

# connection detect function
detect ()
{
    # get the system's default route
    defroute=`route | grep 'default' | awk '{$1=$1;print}' | cut -d ' ' -f2`
    if ping -t1 -c1 $defroute > /dev/null 2>&1; then
        status="connected"
    else
        status="disconnected"
    fi
}

# decide whether to connect or disconnect
detect
if [ "$status" == "connected" ]; then
    echo "Active!  Shutting down..."
    poff
else
    echo "Not active!  Starting..."
    pon
fi
exit 0

```
Depending on how you want to determine if the connection is active or not, you can replace the 'detect' function's code with some connection detection code of your choosing.  In this example, I get the default route and then ping it.  If the ping gets a response, the connection is considered active.  If it times out, the connection is considered inactive.  I just used this method off the top of my head.  There are probably better ways to do it but at least this gives you an example to work with.  Good luck.

---

### Post by perixx on 2007-11-04
Thanks a lot, Robert!

I'll have a look at it tomorrow, too tired now...

perixx

---

### Post by perixx on 2007-12-04
Hello again, robert_pectol!


I hope you'll read this... it's been some time since you've sent along the start/stop script for networking; I hadn't got the possibility to check until now.

It seems there are some problems with this method:

- Firstly, I need to disable the automatic DSL-connection at startup.
My /etc/network/interfaces file looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet ipv4ll

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

```

Now, the only time your script seems to be at least partially functioning is, when I comment out the line 'auto dsl-provider'; I won't have Inet access till I run your script once. BUT connection isn't being cut when starting the script again!

What's more, I needed to change the pon/poff commands to 'pon/poff dsl-provider' or else I would get the error:
> sh ToggleNet
[: 31: ==: unexpected operator
Not active!  Starting...
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
 
The message 
> [: 31: ==: unexpected operator
Not active!  Starting...
Plugin rp-pppoe.so loaded.
 is displayed every time I start the script, regardless of the network's status - I have no idea why!

Additionally, the LAN-connection is already up and running (auto eth0) at booting time and I don't want that; I'd rather like to have everything set up correctly and only trigger the LAN connection, if needed (with ifconfig eth0 up/down ?). But commenting out 'auto eth0', the Inet connection is triggered at boot-up inspite...

Can you give some advice please? Or someone else?


perixx

---

### Post by perixx on 2007-12-05
*bump*

---

### Post by perixx on 2007-12-06
*bumpagain*

---

### Post by toxin on 2007-12-06
I had the same need and wrote a very trivial and dirty script. You could use it while waiting for a more advanced solution :)

```

#! /bin/bash

if `pidof pppd`; then
   poff provider
else
  pon provider
fi

```

P.S. I ended up using ppptray, perhaps you could give it a try ([link]("http://ubuntuforums.org/showthread.php?t=534709") to discussion).

---

### Post by perixx on 2007-12-06
Thanks, Toxin!

I'd feel better with switching on/off my eth0 connection in the first place, but better than nothing...

Do you happen to know how to disable the automatic network connection at boot?

perixx

---

### Post by perixx on 2007-12-09
> #! /bin/bash

if `pidof pppd`; then
   poff provider
else
  pon provider
fi

hm... your script doesn't work for me, or I'm doing it wrong.
I figured that you wanted me to put my process number (PID) in for 'pidof', with 4 digits. But it didn't work, it says: '[number] not found, rppppoe.so loaded'. 

Or do I JUST have to use the number without 'pppd'? haven't tried that yet...

PPPtray looks promising but it only started the first time and now it won't anymore at all, even though I've completely removed and re-installed it. Maybe there's sth. wrong with python?

perixx

---

### Post by perixx on 2007-12-09
*bump*

---

### Post by perixx on 2007-12-10
I can't get either of those scripts working... is there something I need to specifiy within the code lines?
That means, the recognition whether network is up and running or not won't function.
perixx

---

### Post by perixx on 2007-12-12
*bumpabing*

---

### Post by perixx on 2007-12-14
*bumpagain*

---

### Post by toxin on 2007-12-23
Hi perixx, sorry for the long delay but this forum is really overposted, topics go to the 2nd-3rd page in a couple of hours and I often overlook them :(
As for the script I posted, it doesn't work because there's an error, the right syntax is the following (really sorry):

```

#!/bin/bash
if pidof pppd
        then poff YOUR_PROVIDER
        else pon YOUR_PROVIDER
fi

```

So the deal was the ` chars. It should work now...

As for switching off the network connection, I am not sure I understand what you mean, cause I connect to the internet through an USB modem (so a ppp0 logical device, I guess) and killing pppd is enough to me.
Maybe you mean something like the command: "sudo ifconfig eth0 down"?

---

### Post by perixx on 2007-12-23
Hy toxin!

Thank you for the reply -- better late than never ;)
Your script works very well now...!
Of course I'd prefer some more comfort (with traffic control) like ppptray, but it doesn't work. I haven't figured out why....

Anyway, now I can start/stop with a single click on my tray-starter which triggers the little script. Great!
As for 'sudo ifconfig eth0 up/down', I've tried that before, but you need to 'sudo' and enter password every time, so that's not practicable (would be a 'cleaner solution' when combined with '&& sudo ifconfig eth0 down'). Perhaps you know how to switch on/off 'eth0' without ifconfig and having to sudo??

perixx

---

### Post by toxin on 2007-12-23
Hi, I'm glad it finally worked :)

As for the password, in one of your previous posts you mentioned that you wanted to prevent the network to be turned on on boot. I don't know how to prevent, but you could insert the line "ifconfig eth0 down" in /etc/rc.local, before the line "exit 0". This way you won't be prompted for the password as rc.local is executed on boot as root.

Another solution would be to configure sudo not to prompt you for the password when executing ifconfig.  Something like:

```
your_user_name ALL= NOPASSWD: ifconfig
```

in /etc/sudoers should do the trick. 
**man sudoers** for more info. Maybe you'll have to put the full path for ifconfig in sudoers. (**EDIT:** See [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_have_Firestarter_start_without_the_root_password"). It's meant for firestarter, so replace firestarter with ifconfig ;) )

P.S. ppptray: have you configured it to use the right conf file in /etc/ppp/peers? It doesn't do much more than launching pon provider so it's weird it doesn't work for you... when you reinstalled it have you deleted .ppptrayrc (or something similar) in your home dir?

---

### Post by perixx on 2007-12-25
Hy toxin!

Hm, don't you think it's a bit uncommon (=risky) to strip password-request from the 'ifconfig' command?

Tried to install 'ppptray' again, btw... at first, the config-dialog shows up and I can select my connection; after acknowledging, there's nothing more happening and the terminal stays in progress. Hitting CTRL-C will break the loop and reply:
> /usr/bin/ppptray
Traceback (most recent call last):
  File "/usr/bin/ppptray", line 26, in <module>
    ppptray.main()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 526, in main
    self.poll()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 435, in poll
    time.sleep(0.1)
KeyboardInterrupt

I also attempted to 'gksudo' it - no reaction apart from the message above isn't shown...

perixx

---

### Post by perixx on 2008-01-09
Hello again... I've decided to stick to 'PPPTRAY', as was suggested above, it's small, simple, gives feedback and does what I need - apart from disconnecting my LAN conncetion (Thanks for the hint!):
[http://ubuntuforums.org/showthread.php?t=534709]("http://ubuntuforums.org/showthread.php?t=534709")

perixx

---

