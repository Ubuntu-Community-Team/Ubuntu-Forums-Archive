---
title: "First day on Ubuntu - tried to load media plugins: Software Index is Broken?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by texla on 2009-08-14
OK - no idea what's up -  I tried to get the media files working on my first ubuntu day and it went wrong.  I used this how to: 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

Then I copied the info into my Terminal for 32 bit Ubuntu 8.1 and higher (I have the current 9.04) After I pressed enter, it all seemed to be loading and I came back a half hour later.  There was a message agreement from Sun there with an ok at the bottom.  I tried everything to click or enter the ok but nothing happened.  So i tried to close the terminal but I received a warning that there was a process running.  I tried some more but i did end up closing the terminal.  Now i can't install any flash from the websites or even add the restricted-formats-pack from here: **[Click here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")** When I try, I get a message that my **Software Index is Broken.**

So what's up?  Do I need to reinstall ubuntu now or is there a fix?  I looked over the ubuntu kung fu manual and nothing remotely connected to this issue is in it - Any tips on what should I do?  Also, any good tutorials on what the Terminal process is all about?

thanks

---

### Post by ibizatunes on 2009-08-14
hello and welcome,
what you need is Medibuntu to play restricted formats


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

also do the following commands 
application > acessories > termainal - paste the code below

```
sudo apt-get install ubuntu-restricted-extras
```

this will install flash and mp3 codecs etc

---

### Post by texla on 2009-08-14
> **ibizatunes said:**
> hello and welcome,
what you need is Medibuntu to play restricted formats


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

ALSO Do that also do the following commands 
application > acessories > termainal - paste the code below

```
sudo apt-get install ubuntu-restricted-extras
```this will install flash and mp3 codecs etc

OK thanks but I tried both the terminal adding of medibuntu code from the above link and also going to software sources to click on allowing Medibuntu - both times I get this error message

** dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. **

help

---

### Post by konqui on 2009-08-14
Before you do what the previous reply said run

sudo apt-get install -f


This will fix software index.

---

### Post by ibizatunes on 2009-08-14
Normally this happens if a install or update failed, normally caused by turn off your pc when it installing or somthing like that
Anyway to fix it

in the terminal run this command
```
sudo dpkg --configure -a
```
then, if the above doesnt work
```
sudo apt-get install -f
```

---

### Post by texla on 2009-08-14
> **konqui said:**
> Before you do what the previous reply said run

sudo apt-get install -f


This will fix software index.
just tried that - got this message again:
**E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. **

---

### Post by texla on 2009-08-14
> **ibizatunes said:**
> Normally this happens if a install or update failed, normally caused by turn off your pc when it installing or somthing like that
Anyway to fix it

in the terminal run this command
```
sudo dpkg --configure -a
``` 


ok - it looks like that did something good! - it says registering documents with scrollkeeper - 
now should I go do the medibunto terminal add or restricted pack or what?

---

### Post by ibizatunes on 2009-08-14
Now run 
```
sudo apt-get ubuntu-restricted-extras
```
then medibuntu

then you should be ok

Post any other issue up on the forums and you normally get some help
And stick with linux it hard at first but in the end WELL worth it

---

### Post by texla on 2009-08-14
> **ibizatunes said:**
> Now run 
```
sudo apt-get ubuntu-restricted-extras
``` 

just did that - got this error:
E: Invalid operation ubuntu-restricted-extras

am I supposed to do something other than just copy and past the code into the terminal?

---

### Post by ibizatunes on 2009-08-14
```
sudo apt-get install ubuntu-restricted-extras
```

forgot the install bit
that should fix it

---

### Post by texla on 2009-08-14
> **ibizatunes said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```forgot the install bit
that should fix it
Well - something happened this time but it still looks wrong says this at the end:

Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So then i tried to run just the " apt-get -f install "  and it says:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

any ideas? thanks for your help

---

### Post by texla on 2009-08-14
whoops

---

### Post by texla on 2009-08-14
> **ibizatunes said:**
> Normally this happens if a install or update failed, normally caused by turn off your pc when it installing or somthing like that
Anyway to fix it

in the terminal run this command
```
sudo dpkg --configure -a
```then, if the above doesnt work
```
sudo apt-get install -f
```
Oh - wait a minute - I forgot the sudo before like you have here - looks like it's going to add 113 mb worth of stuff - cool!  I'll be back if I get stuck with the Sun message again or something else fun

don't worry - nowhere near giving up on linux!

Thanks

---

### Post by texla on 2009-08-14
Alright back again - I have the Sun info blue box in my terminal now and nothing else - it says ok on the bottom of each page but it's not clickable or anything else - Am i just supposed to wait now?  Should I be able to see if anything is happening?  


&#9474;                                                                           &#9618; Configuring sun-java6-bin

 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618; 
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618; 
 &#9474;                                                                           &#9646; 
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>

---

### Post by Cheesemill on 2009-08-14
Hit TAB to highlight the button and hit Enter, exactly the same as Windows!

---

### Post by texla on 2009-08-14
> **Cheesemill said:**
> Hit TAB to highlight the button and hit Enter, exactly the same as Windows!
Thanks! Whew... 

by the way - is there something that will notify me when this is done?  It has already gone back to the desktop cursor.  Anyhere else I should be going to monitor if anything is being loaded so I don't interrupt process again?

also says:

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

right above cursor (but no error messages yet!)

---

### Post by thiebaude on 2009-08-14
Or if tab doesn't work, try tab and shift at the same time.

---

### Post by texla on 2009-08-14
> **thiebaude said:**
> Or if tab doesn't work, try tab and shift at the same time.
Dig it - tab worked great - just wondering if I can close the terminal or how to know if this is done - I feel like it is but these things don't always work with feelings - and do I need to load something else now or am I good to ge?

---

### Post by sydbat on 2009-08-14
You'll know it's done when you get this:```
you@you-desktop:~$ 
```

---

### Post by texla on 2009-08-14
> **sydbat said:**
> You'll know it's done when you get this:```
you@you-desktop:~$ 
```
Thanks a lot!  Closed it and moving on the restricted pack - appreciate the help from all!

---

