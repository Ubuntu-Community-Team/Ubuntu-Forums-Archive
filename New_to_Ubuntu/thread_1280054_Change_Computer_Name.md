---
title: "Change Computer Name"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by Jason Cook on 2009-10-01
I am trying to change my computer name. I am receiving errors.

I type
```
sudo gedit /etc/hostname
```
Then I receive this error
```
sudo: unable to resolve host Jason Cook
No protocol specified

(gedit:7990): Gtk-WARNING **: cannot open display: :0.0
```
What am I doing wrong and how can I fix it?

--
Jason Cook

---

### Post by sancho panza on 2009-10-01
I cannot make sense of the error either, but try if
```
gksudo gedit /etc/hostname
``` works.

---

### Post by jonobr on 2009-10-01
Hello


I would also check your /etc/hosts file to see if you have any name mapping going on in there with your old name.


You should also make backups of any files you modify in case you make a mistake.

If you having problems exporting gui displays you could always use vim
a common text editor

---

### Post by Jason Cook on 2009-10-01
> **sancho panza said:**
> 
 ```
gksudo gedit /etc/hostname
```

I tried that and I recieved this error:
```
/usr/share/themes/EdubuntuColors/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
No protocol specified

(gedit:18283): Gtk-WARNING **: cannot open display: :0.0
```

---

### Post by Jason Cook on 2009-10-01
> **jonobr said:**
> 
I would also check your /etc/hosts file to see if you have any name mapping going on in there with your old name.


This is what the /etc/host file says

```
127.0.0.1    Jason Cook    localhost.localdomain    localhost
127.0.1.1    ONONWARA

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```My computer name now is "Jason Cook" it was "ONONWARA"

---

### Post by Jason Cook on 2009-10-01
I just noticed no that whenever I use "sudo" I am receiving this error.
```
sudo: unable to resolve host Jason Cook
```I changed my computer name yesterday and receive this error (I haven't received this error before).

---

### Post by jonobr on 2009-10-01
Yep your screwing up your name resolution here.

The hoistname is an important part of a linux/unix  system.

When you enter 'jason cook' as your hostname its looking at that as have two name entries for 127.0.0.1 
so Im sure if you ping jason, it would work, if you ping cook it would work,

IMO you need to have one name like jasoncook or jcook

---

### Post by Iowan on 2009-10-01
You need to change both /etc/hosts AND /etc/hostname - otherwise (as you've discovered) **sudo** complains. Rescue CD may be the easiest way to fix things.

---

### Post by Jason Cook on 2009-10-01
> **Iowan said:**
> You need to change both /etc/hosts AND /etc/hostname - otherwise (as you've discovered) **sudo** complains. Rescue CD may be the easiest way to fix things.


What Rescue CD should I use? I am using a netbook so it must be able to boot from a USB stick.

---

### Post by jonobr on 2009-10-01
Its looking as if your display is having issues.
if you can login then use vim to change these files,Heres how you can change the name,
BUT MAKE A BACKUP OF THEM FIRST!!!!!!
 I recommend practicing on a test file first so you are happy with how vim works.

You start by entering in the terminal window 

sudo vim /etc/hosts

This is an important file so again , have a backup and backout if you make mistakes

Using vim as a text editor takes a bit of getting used to, but you can control where your cursor is by the arrow keys,
You initially enter into what is called command mode by default

when you get to the line or text you want to change using the arrows, go to the first character .

Pres x to delete one character at a time.
AS you press x the remaining letters are gobbled up toward where your cursor is

When what you have is removed, and you are ready to put in  the name,
hit the i key
i means insert, you have now gone from command mode to insert mode.
The bottom should show the word insert.
Type in the new hostname.

when the new name is in there.
escape from command mode by hitting escape.
You know your there as the 'insert' at the bottom disappears.

If your NOT happy with the change or your want to exit at any point
hit 

```
:q!
```

(colon q exclamation)
This closes the file without saving

If you are happy then you can save by 
```
:wq!
```
(write and quit)

Do the same name for both files, no spaces or special characters.

If it matches and they look the same, the reboot (easiest) and all should be ok

---

### Post by CatKiller on 2009-10-01
> **Jason Cook said:**
> What Rescue CD should I use? I am using a netbook so it must be able to boot from a USB stick.

You should be able to drop to a root shell from the Recovery Mode menu (select it from the GRUB menu). You won't have to use your (broken) sudo then, just

```
nano /etc/hosts
nano /etc/hostname
```

to make them agree on what the computer is called. (Ctrl-O to save, Ctrl-X to exit, *shutdown -r now* to restart the computer when you're finished)

It used to be easy to do this graphically through the old network tool, but since the switch to NetworkManager this is one of the functions that hasn't made it back in. I hope it happens soon.

---

### Post by Jason Cook on 2009-10-02
I tried using vim. I was able to sucessfully change the name. Whenever I use sudo I still recieve this error:
```
sudo: unable to resolve host ONONWARA
```
If I try to use gedit to change my name I get this error
```
/usr/share/themes/EdubuntuColors/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
```
but gedit will still open.

---

### Post by jonobr on 2009-10-02
Hello


I was thinking about this problem last night as Iowan's response was different to mine.

Iowan is a frequent and gifted poster and I was wondering why he recommended using the live cd.

Rereading the post this morning, I see you have sudo issues,
No i get why Iowan recommended what he did,

given changing hostnames requires sudo, I would now concur with Iowan

---

### Post by Jason Cook on 2009-10-03
I think that I have solved this.

My /etc/hostname says
```
ONONWARA
```

My /etc/hosts says
```
127.0.0.1    ONONWARA    localhost.localdomain    localhost
```

---

### Post by Iowan on 2009-10-04
Don't argue with success...
The hostname in */etc/hosts* is usually assigned to 127.0.1.1 with 127.0.0.1 left with localhost (and optional localhost.domainname), but I've seen it done this way, too!

---

### Post by Jason Cook on 2009-10-04
I not arguing with the success. I just wanted to know if this was correct
> **Iowan said:**
> Don't argue with success...

Thank you everyone for your help.

---

### Post by jonobr on 2009-10-05
looks good,

your can clarify by just typing hostname in a terminal window

but it looks right....

---

### Post by Iowan on 2009-10-05
> **Jason Cook said:**
> I not arguing with the success. I just wanted to know if this was correct
OOPS! :shock:  
I meant ***_I_*** shouldn't argue with ***_your_*** success...
Congrats on fixing it... :oops: Sorry to leave the wrong impression...

---

