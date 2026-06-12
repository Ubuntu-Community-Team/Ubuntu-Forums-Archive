---
title: "Making a program run"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Nottawa on 2009-10-25
I just installed 9.04 and it was very easy.  Now I am trying to make a program work that I just installed.  I used the add/remove software function and installed Gnucash.  If I click on the icon to start the program, I get the busy indicator for about 15 sec, and then nothing.  Nothing stops working and nothing new starts.  What did I do wrong?  How do I get it to work?

---

### Post by earthpigg on 2009-10-25
hi,

you may not have done anything wrong. it could be ubuntu's fault.

if you open a terminal, and run program from there, what output does it give you?

to find out the terminal command to start the program: right click on the 'applications/places/system' menu -> 'edit menu' -> navigate to gnucash -> right click -> properties -> see what is written in the 'command' field.

run that command in a terminal, and post back what it tells you.

---

### Post by Nottawa on 2009-10-26
Earthpigg: Now I am worried.  I tried what you suggested, starting with finding the terminal command. When I click on "edit menus", nothing happens.  Left or right clicks both just close he window.  Next suggestion?

---

### Post by philinux on 2009-10-26
Open a terminal, Applications>accessories> Terminal.

Type in

```
gnucash
```

Press enter.

Post back any errors.

---

### Post by Nottawa on 2009-10-26
Phil:  Here is the result of entering gnucash as you suggested.  What do I do now?       Thanks, Peter

peter@peter-laptop:~$ gnucash
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

An error occurred while creating the directory:
  /home/peter/.gnucash
Please correct the problem and restart GnuCash.
The reported error was 'No space left on device' (errno 28).
peter@peter-laptop:~$

---

### Post by thomz92 on 2009-10-26
no space left? how big is your hardrive? (check system monitor for info). Did you perhaps make a seperate partition for your home folder and make it too small?

---

### Post by stlsaint on 2009-10-26
whats the size of your (/) partition?

---

### Post by earthpigg on 2009-10-26
hi,

post the output of this, please:
```
df -Th
```

---

### Post by Nottawa on 2009-10-27
I was poking around my system last night after my last post when I realized that my partitions may not be right.  I let the installer set them up, but this appears to have been a mistake.

I have a 250 gig hard drive, and 3 gig ram.  As my partitions are not set up very well, how do I change that and what are some recommendations to make them?  I have a Lenovo Thinkpad and need to keep my Windows partitions (at least for the time being).

Here is the result of the command as requested by Earthpigg:

peter@peter-laptop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3    2.3G  2.3G     0 100% /
tmpfs        tmpfs    1.4G     0  1.4G   0% /lib/init/rw
varrun       tmpfs    1.4G   96K  1.4G   1% /var/run
varlock      tmpfs    1.4G     0  1.4G   0% /var/lock
udev         tmpfs    1.4G  168K  1.4G   1% /dev
tmpfs        tmpfs    1.4G  456K  1.4G   1% /dev/shm
lrm          tmpfs    1.4G  2.7M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs    1.0M   20K 1004K   2% /tmp
peter@peter-laptop:~$

---

### Post by empty_spaces on 2009-10-27
There's your problem - a 2.3GB root partition.
You may have to redo your partitions manually.
If you have Vista, I believe it has an inbuilt utility to resize its partition and free up some space for Ubuntu. Gparted(LiveCD) should also be useful here.

---

### Post by earthpigg on 2009-10-27
> **Nottawa said:**
> 
peter@peter-laptop:~$ df -Th
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3    2.3G  2.3G     0 100% /
```


bingo.

recall when you installed: it said '*guided*' partition, not '*totally automatic*' partition. this throws a lot of folks off. you where supposed to have grabbed the slider and dragged it over to make the ubuntu partition bigger. :D

if you have a dual boot system, take a look [here]("http://gparted.sourceforge.net/faq.php") before resizing partitions - specifically, #9.

if you do ***not*** have a dual boot system (or ***after*** you have read my link above), boot from the live CD 'without making changes' -> system -> admin -> partition editor.

this will start gparted. 

if dual boot or if you have other partitions you want to keep: resize / to be ***at least*** 20gb.
if not dual boot: resize / to be everything except your ~2gb swap partition.


in the future, take a look at "df -Th" from time to time. do not let linux partitions get over 90% full until you have a better understanding of the risks and issues associated with doing so. 

(hint: one of the problems with filling a linux partition over 90% full to, saaaaaaay, 99.X% full like you have, is that things start breaking all over the damn place. this is the price we pay for not needing to defrag.)

---

### Post by Nottawa on 2009-10-27
Thanks for your guidance on this problem.  I am downloading GParted and will give it a go.  As this is a new machine and I have nothing of any value yet, I am not afraid to mess around with the hard drive. I will keep you posted

Peter

---

### Post by Bölvaður on 2009-10-27
when resizing ubuntu do it from the live cd, it has gparted on it.

---

### Post by Nottawa on 2009-10-29
Thanks for all your help.  I got GParted, ran it and enlarged my Linux partition and the swap partition and now I seem to be running alright.  My Gnucash program started right up when I clicked it after rearranging the hard drive

Peter

---

