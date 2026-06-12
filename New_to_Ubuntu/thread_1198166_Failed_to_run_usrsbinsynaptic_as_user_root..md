---
title: "Failed to run /usr/sbin/synaptic as user root."
date: 2009-06-27
forum: New to Ubuntu
---

### Post by GnrPersia on 2009-06-27
Hi,

before I write my problem I wanted to say that I've been using windows for my entire life and it's just 3 days that I've just decided to completely get out of windows and start to work with ubuntu.

so far everything was fine until today after updating something and messing around with "gksudo" commands restarted my comp and now I get this problem when I want to run synaptic package manager that a window appears with the following comments:

[B]"Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."[/B]

something is not letting me even go to system > users and groups as well as lots of other places. 

also I thought that this might be useful to help me in the case:

in terminal:

[B]adel@aDell:~$ sudo synaptic package manager
[sudo] password for adel: 
adel is not in the sudoers file.  This incident will be reported.[/B]


Please help me because I don't want to get disappointed with this one and step back to windows. :(


many thanks

Adel

---

### Post by nhasian on 2009-06-27
actually the command is just

```
sudo synaptic
```

if you need to edit your sudoers list you do it with this command:

```
sudo visudo
```

you can read more about that [here]("https://help.ubuntu.com/community/Sudoers")

---

### Post by kerry_s on 2009-06-27
boot into the rescue mode and run> **visudo**
add: **adel ALL=(ALL) ALL**

---

### Post by kixome on 2009-06-27
sudo visudo

add: username ALL=(ALL) ALL  under the user privelages section

then press ctrl+o to save
and ctrl+x to exit

---

### Post by nhasian on 2009-06-27
Under my user privilege section, which is the default as i havent changed anything, it is:

```
# User privilege specification
root    ALL=(ALL) ALL

```

and if depending on which editor you chose, the command to save my be different.  for example in vi to save just press ESC to enter command mode, then ZZ to save.  alternatively, after ESC you can type :wq for command, write, quit.

---

### Post by GnrPersia on 2009-06-27
> **nhasian said:**
> actually the command is just

```
sudo synaptic
```if you need to edit your sudoers list you do it with this command:

```
sudo visudo
```you can read more about that [here]("https://help.ubuntu.com/community/Sudoers")

outcomes are:

adel@aDell:~$ sudo synaptic
[sudo] password for adel: 
adel is not in the sudoers file.  This incident will be reported.


adel@aDell:~$ sudo visudo
[sudo] password for adel: 
adel is not in the sudoers file.  This incident will be reported.
adel@aDell:~$

---

### Post by GnrPersia on 2009-06-27
> **kerry_s said:**
> boot into the rescue mode and run> **visudo**
add: **adel ALL=(ALL) ALL**

I'm going to try this now. will write you the results.

---

### Post by kixome on 2009-06-27
make it look like this
# User privilege specification

root  ALL=(ALL) ALL
adel  ALL=(ALL) ALL

---

### Post by kixome on 2009-06-27
> **nhasian said:**
> Under my user privilege section, which is the default as i havent changed anything, it is:

```
# User privilege specification
root    ALL=(ALL) ALL

```

and if depending on which editor you chose, the command to save my be different.  for example in vi to save just press ESC to enter command mode, then ZZ to save.  alternatively, after ESC you can type :wq for command, write, quit.

Thats why i specified visudo which should run nano by default, in which my commands were correct.

---

### Post by GnrPersia on 2009-06-27
> **kixome said:**
> make it look like this
# User privilege specification

root  ALL=(ALL) ALL
adel  ALL=(ALL) ALL

perfect! now I can access the synaptic package manager without any problem. :D

**[b]But** [/B]Still I can't have access to System -> Administration -> Users and Groups.

a window appears with the following message:

[b]The configuration could not be loaded
You are not allowed to access the system configuration.[/b]  :(

---

### Post by kixome on 2009-06-27
sudo users-admin

---

### Post by kixome on 2009-06-27
oh, did you restart the system, try that and let me know

---

### Post by kerry_s on 2009-06-27
> **GnrPersia said:**
> perfect! now I can access the synaptic package manager without any problem. :D

**[b]But** [/B]Still I can't have access to System -> Administration -> Users and Groups.

a window appears with the following message:

[b]The configuration could not be loaded
You are not allowed to access the system configuration.[/b]  :(

press> **unlock**
type in your password.

---

### Post by kixome on 2009-06-27
> **kerry_s said:**
> press> **unlock**
type in your password.
Genius, I must be a tard

---

### Post by kixome on 2009-06-27
sorry

---

### Post by kixome on 2009-06-27
asdg

---

### Post by GnrPersia on 2009-06-27
> **kixome said:**
> oh, did you restart the system, try that and let me know

yes I've restarted and like I said synaptic package manager worked fine but users and groups didn't.

> **kixome said:**
> sudo users-admin

now users and groups worked fine with this command and user's setting window appeared

> **kerry_s said:**
> press> **unlock**
type in your password.

but unlock button is not working in the users window and is un-clickable if you get what I mean. but I could work with it way back before all these problems happen :(

---

### Post by kixome on 2009-06-27
Do the users and groups command and give yourself all the rights allowable, other than that I am not sure why auto sudo isn't working

---

### Post by GnrPersia on 2009-06-27
> **kixome said:**
> Do the users and groups command and give yourself all the rights allowable, other than that I am not sure why auto sudo isn't working

users and groups command? you mean "sudo users-admin" ?

---

### Post by kixome on 2009-06-27
sorry ,yes, i was multi posting, dot that and open your properties, then select all the privelages check boxes

---

### Post by GnrPersia on 2009-06-27
> **kixome said:**
> sorry ,yes, i was multi posting, dot that and open your properties, then select all the privelages check boxes

I think It's better to see the situation yourself:

[IMG]http://www.freeimagehosting.net/uploads/4c07b7ff6e.png[/IMG]

---

### Post by kixome on 2009-06-27
try this

gksu
when it opens select your name as the user and run users-admin

---

### Post by kixome on 2009-06-27
You should now be able to unlock it, yo have good taste, I notice you are using the same theme as me, other than the dock at the bottom

---

### Post by GnrPersia on 2009-06-27
oh, ok now I clicked on my user account name and the properties just appeared clickable but others like unlock etc still remained the same. anyways I go to properties and then user privileges but I can not tick on any of the options they're all in grey dead color like the unlock button.

---

### Post by kixome on 2009-06-27
wait a tick, let me reference something

---

### Post by GnrPersia on 2009-06-27
> **kixome said:**
> try this

gksu
when it opens select your name as the user and run users-admin

no way, I do this one too but still the same like "sudo users-admin" command.

I know that I'm making you nervous! :confused: :D


> **kixome said:**
> You should now be able to unlock it, yo have good taste, I notice you are using the same theme as me, other than the dock at the bottom

thnx :)   well it was really hard for me to even figure out how to install themes and docks and spent one whole day on this! but now this user account problem is really making me disappointed but I don't want to retreat!

---

### Post by kixome on 2009-06-27
Nope, nothing there, I cant find what I was looking for, I recommend starting a new thread using this screen shot, and by default even my sudoers file has only root=all...

---

### Post by GnrPersia on 2009-06-27
> **kixome said:**
> Nope, nothing there, I cant find what I was looking for, I recommend starting a new thread using this screen shot, and by default even my sudoers file has only root=all...


ok thanks. at least you could help me run synaptic which is an essential thing for ubuntu.

I appreciate your help and will make another thread with the screenshot.

thanks again. :D

---

### Post by kerry_s on 2009-06-27
> but unlock button is not working in the users window and is un-clickable if you get what I mean. but I could work with it way back before all these problems happen 

look in synaptic, make sure you have policykit-gnome installed.
if thats installed, then you are probably not in the group you need to be in.
so check that first and let us know, then i'll talk you through the group thing.

---

### Post by kixome on 2009-06-27
thank you kerry_s aas i must go to bed and i am no expert, was hitting a brick wall here. Gave it my best shot though, cant kill a man to try. Sorry I couldn't help more
GnrPersia GOOD LUCK, I'm sure you wont need it

---

### Post by GnrPersia on 2009-06-27
> **kerry_s said:**
> look in synaptic, make sure you have policykit-gnome installed.
if thats installed, then you are probably not in the group you need to be in.
so check that first and let us know, then i'll talk you through the group thing.

I'll take a look now wait...

---

### Post by GnrPersia on 2009-06-27
yes this I've searched policykit-gnome and it's installed. also there are some other things similar to it that I see are already installed. 

the description is: "PolicyKit-gnome provides a D-Bus session bus service that is used to
bring up authentication dialogs used for obtaining privileges.

Canonical provides critical updates for policykit-gnome until October 2010."

---

### Post by kerry_s on 2009-06-27
alright, thats take a look at your group file.

press **alt+f2**
type> **gksudo gedit /etc/group**

post that here.

---

### Post by GnrPersia on 2009-06-27
> **kerry_s said:**
> alright, thats take a look at your group file.

press **alt+f2**
type> **gksudo gedit /etc/group**

post that here.


```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:
ssl-cert:x:105:
lpadmin:x:106:
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
gdm:x:111:
netdev:x:112:
saned:x:113:
pulse:x:114:
pulse-access:x:115:
pulse-rt:x:116:
messagebus:x:117:
polkituser:x:118:
avahi:x:119:
haldaemon:x:120:
admin:x:121:
adel:x:1000:
sambashare:x:122:
winbindd_priv:x:123:
debian-tor:x:124:
```

sorry for the delay

---

### Post by kerry_s on 2009-06-27
how the heck? you aren't in any groups, thats not good.
try these:
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
**dialout:x:20:adel**
fax:x:21:
voice:x:22:
[B]cdrom:x:24:adel
floppy:x:25:adel[/B]
tape:x:26:
**sudo:x:27:adel**
**audio:x:29:pulse,adel**
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
**video:x:44:adel**
sasl:x:45:
[B]plugdev:x:46:adel
staff:x:50:adel[/B]
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:
ssl-cert:x:105:
lpadmin:x:106:
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
gdm:x:111:
netdev:x:112:
saned:x:113:
pulse:x:114:
pulse-access:x:115:
pulse-rt:x:116:
messagebus:x:117:
polkituser:x:118:
avahi:x:119:
haldaemon:x:120:
**admin:x:121:adel**
adel:x:1000:
sambashare:x:122:
winbindd_priv:x:123:
debian-tor:x:124:

```

---

### Post by GnrPersia on 2009-06-27
problem Solved! now I can unlock my user account and just ticked all of the privileges for my account. I don't know if it's right or not anyway!

thanks a lot kerry. I'll never remember your help. :D =D>

and thank you too kixome.

---

### Post by kerry_s on 2009-06-27
> **GnrPersia said:**
> problem Solved! now I can unlock my user account and just ticked all of the privileges for my account. I don't know if it's right or not anyway!

thanks a lot kerry. I'll never remember your help. :D =D>

and thank you too kixome.

that's good, now i can get some sleep, its 2am here. :D

---

### Post by GnrPersia on 2009-06-27
> **kerry_s said:**
> that's good, now i can get some sleep, its 2am here. :D

ok. have a good sleep and nice dreams dear. :)

---

