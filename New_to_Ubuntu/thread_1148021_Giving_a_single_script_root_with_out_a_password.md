---
title: "Giving a single script root with out a password"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-05-03
I have a script I have to run to make my 3g modem work how ever it needs root privileges to run properly. Is there a way I can allow this script to run in root with out prompting the user to give a password? I have people that use my netbook who need to turn on the 3g but who don't need my root password.

~Jeff

---

### Post by kerry_s on 2009-05-04
sudo visudo

add:
%users ALL=(ALL) NOPASSWD: /path/to/script

you still have to use sudo, but it won't ask for a password.
example:
sudo script

---

### Post by SunnyRabbiera on 2009-05-04
Just remind the dangers of doing this, there is nothing more dangerous then passwordless systems.

---

### Post by kerry_s on 2009-05-04
> **SunnyRabbiera said:**
> Just remind the dangers of doing this, there is nothing more dangerous then passwordless systems.

he said script, not system, he does not want to share the password.

---

### Post by beastrace91 on 2009-05-04
Thank you much Kerry, worked like a charm.

~Jeff

---

### Post by beastrace91 on 2009-05-04
It looks like I spoke too soon... Here is my sudo visudo file:

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%user ALL=(ALL) NOPASSWD: /home/jeff/.flipflop.sh

```

And here is my command I am running:

```
sudo /home/jeff/.flipflop.sh
```

How ever when it pops up a terminal to run the script it still asks me to enter a root password :/ Any ideas what I am doing wrong?

Thanks,
~Jeff

---

### Post by kerry_s on 2009-05-04
you missed the "s" on users.

```
%user ALL=(ALL) NOPASSWD: /home/jeff/.flipflop.sh
should be:
%user**s** ALL=(ALL) NOPASSWD: /home/jeff/.flipflop.sh
```

---

### Post by tommynz1975 on 2009-05-04
I would have the attributes for your script owned by admin or your self  so no one could edit the script.......   ie some one up to mischief could re-write the script...  

the script that needs NO password.

I am sure you know this all ready, but it wont hurt to remind.

---

### Post by beastrace91 on 2009-05-05
Good suggestion Tommy, but I am going to count on the fact that the people using my laptop A. aren't smart enough to look for hidden files, B. Typically are windows users and don't know anything about bash, and C. Like my computer to stay working so they can use it :)

~Jeff

---

### Post by KIAaze on 2009-05-05
I would still follow tommynz1975's advice. The script needs to be run as root, so give it to root by putting it in /root and doing a chown root:root + chmod 700 on it.

It's very easy to get the location of such a weak point on a system by running "sudo -l" (doesn't require any password). So a malicious user or script or any potential virus could exploit this weakness!

---

### Post by beastrace91 on 2009-05-05
Heeding your words KIA I did the following:

1. Moved .flipflop.sh to my / directory

Then in console I ran:

```
chown root:root .flipflop.sh
chmod 700 .flipflop.sh
```

How ever it appears I am back to square one as it is once more asking me for my root password to run the script, here is my visudo file: > Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%users ALL=(ALL) NOPASSWD: /.flipflop.sh


What am I doing wrong?

~Jeff

---

### Post by kerry_s on 2009-05-05
put it in /bin, bin is where the executables are.
unhide it, remove the "."

```
**%users ALL=(ALL) NOPASSWD: /bin/flipflop.sh **
```

---

### Post by aysiu on 2009-05-05
How about instead of having the user run it, you put it in /etc/init.d along with all the other system startup scripts, if it's something you want to run for all users?

---

### Post by beastrace91 on 2009-05-05
Is there a way I can have it auto run only when it detects a device is plugged in? I only need the script activated when Modem is plugged in.

~Jeff

---

### Post by beastrace91 on 2009-05-05
I did the following and it is still asking for the root password when I run the script:

```
cd /
sudo mv .flipflop.sh /bin/flipflop.sh
```

New visudo > %users ALL=(ALL) NOPASSWD: /bin/flipflop.sh


Ideas?

~Jeff

---

### Post by KIAaze on 2009-05-05
Have you added yourself to the "users" group? ;)
And don't forget to add all other users to it too.

Add user to group through GUI:
System->Administration->Users and groups
Or by command-line:
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

You could also just let all users (even if they don't belong to the "users" group) run the script without a password by putting this in /etc/sudoers:
```
ALL ALL=(ALL) NOPASSWD: /.flipflop.sh
```

But using a group is obviously safer. :)

Just for your information: The syntax is:
```
USER/GROUP MACHINE=(runas) NOPASSWD: /.flipflop.sh
```

So a maximum security sudoers line to allow only user "joe" on only the machine "joe-desktop" to run the script without a password only as user "root" would be:
```
joe joe-desktop=(root) NOPASSWD: /.flipflop.sh
```
(To run a command with sudo as a different user, use "sudo -u USER COMMAND".)

Of course, just making sure the script is written in a safe way (no relative paths, no environment variables, etc) and can't be modified or read (you can set the permissioons to 100 instead of 700) is already safe enough I think.

---

### Post by kerry_s on 2009-05-05
> **beastrace91 said:**
> I did the following and it is still asking for the root password when I run the script:

```
cd /
sudo mv .flipflop.sh /bin/flipflop.sh
```

New visudo 

Ideas?

~Jeff


i bet /bin is not in the path for users, try /usr/local/bin

as for the script auto run, is the modem plugged in at boot or after boot?

you can try putting it in /etc/rc.local which is run as root on startup.
example:
**/usr/local/bin/flipflop.sh >/dev/null 2>&1 &**

the " >/dev/null 2>&1 & " is so it will quietly continue if you don't have the modem plugged in.

you still should try and get the sudo working in case you have to do it after it's booted.

---

### Post by beastrace91 on 2009-05-06
The modem is almost always plugged in after booting thus the need for getting the script working, I'll play around with placement of the file/visudo settings and post back if I get it working or not later this evening.

~Jeff

---

### Post by kerry_s on 2009-05-06
> **beastrace91 said:**
> The modem is almost always plugged in after booting thus the need for getting the script working, I'll play around with placement of the file/visudo settings and post back if I get it working or not later this evening.

~Jeff

can you post the script? if we could see what it was doing, perhaps we could come up with a way to automate it.

---

### Post by beastrace91 on 2009-05-06
Here is the script, it is pretty simple. It just runs usb_modeswitch to tell Ubuntu that my USB device is indeed a modem and not a CD drive.

```
/usr/sbin/usb_modeswitch
sleep 10
usb_modeswitch -v 0x1f28 -p 0x0020 -R 1
```

~Jeff

---

### Post by kerry_s on 2009-05-06
i took a look at usb_modeswitch and they have a section to help, have you tried any of that?
[http://www.draisberghof.de/usb_modeswitch/#automate](http://www.draisberghof.de/usb_modeswitch/#automate)

---

### Post by beastrace91 on 2009-05-07
Yea I took a peek through that but I couldn't figure out how to get udev to run my flipflop script when I hooked in the device, the examples there are for running just usb_modeswitch when you hook in your device, but my Cricket is strange and requires a short delay followed by a hard reset for the network manager to detect it, thus my little script. Is there a way I can udev auto run my script when it detects a certain PID/VID is hooked in?

~Jeff

---

### Post by KIAaze on 2009-05-07
Have you tried adding yourself to the "users" group and use this sudoers file:
```
Defaults env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%users ALL=(ALL) NOPASSWD: /.flipflop.sh 
```

while having the script in /.flipflop.sh and with 700 as permissions and owned by root?

---

### Post by beastrace91 on 2009-05-07
I did get the script working with out asking for my root password, the issue was that I needed to add myself to the users group :)

Thank you much!
~Jeff

---

### Post by KIAaze on 2009-05-07
Ah ok. Because I had suggested this in my previous post already and it seemed like it didn't work which would have been strange since I tested it first. :)

---

