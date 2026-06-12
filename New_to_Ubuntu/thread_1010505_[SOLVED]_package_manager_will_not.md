---
title: "[SOLVED] package manager will not"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by shadowlands on 2008-12-13
open nor can I update.  

I am very new to this and any advice would be appreciated .
This is what shows up when I try to open the manger.

'E: Type '--19:26:47-- is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

---

### Post by taurus on 2008-12-13
There is something wrong with the medibuntu's repo.  You need to edit it

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and place a # in front of every line in there to comment them all out.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

Don't forget to close down update-manager first before you run those two commands from a terminal.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by shadowlands on 2008-12-13
Thank you for responding to me!!  Kay, I did as you as you advised and a medibuntu.list page came up and the page is blank.  Was I supposed to look at something else on that page.  [/B]> **taurus said:**
> There is something wrong with the medibuntu's repo.  You need to edit it

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and place a # in front of every line in there to comment them all out.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

Don't forget to close down update-manager first before you run those two commands from a terminal.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by drs305 on 2008-12-13
> **shadowlands said:**
> I did as you as you advised and a medibuntu.list page came up and the page is blank.  Was I supposed to look at something else on that page.  [/B]

Normally a blank file is created when the command is run with a non-existent filename. Are you sure you typed it correctly? Cut & Paste is usually the preferred method of running forum commands.

If you are sure you typed it correctly, run this to ensure the file /etc/apt/sources.list.d/medibuntu.list actually exists:
```
ls /etc/apt/sources.list.d
```

---

### Post by shadowlands on 2008-12-13
Thank you for assisting me!  I put the info in wrong this time  my page is not blank 

**/ is a directory.**

is the message that appears along with the following statement:
 
**Please check that you typed the location correctly and try again.**

to the left of the message is a red circle with a white minus in the middle of the circle.

Confused**

I placed the code in the run applications box that appears after you hit alt and f2 and I received a different message 

[B]
--19:26:47--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list.2'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

    0K                                                       100%   14.09 MB/s

19:26:48 (14.09 MB/s) - `hardy.list.2' saved [226/226][/B]




is this where I place the # in front of the --19?





> **drs305 said:**
> Normally a blank file is created when the command is run with a non-existent filename. Are you sure you typed it correctly? Cut & Paste is usually the preferred method of running forum commands.

If you are sure you typed it correctly, run this to ensure the file /etc/apt/sources.list.d/medibuntu.list actually exists:
```
ls -la /etc/apt/sources.list.d
```

---

### Post by taurus on 2008-12-13
Just remove all the lines in there since they are all wrong.

---

### Post by drs305 on 2008-12-13
Let me make sure I understand you. When you run the 'gedit' command a file opens and this is what is in the file?
```

--19:26:47-- http://www.medibuntu.org/sources.list.d/hardy.list
=> `hardy.list.2'
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]
0K 100% 14.09 MB/s
19:26:48 (14.09 MB/s) - `hardy.list.2' saved [226/226]

```

Even if not, let's just recreate the medibuntu sources.list entry. We will rename that file for backup purposes and replace it by running the following commands:
```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bad
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get upgrade

```

This assumes you are running Hardy Heron.
**Added**: In ubuntu, the easiest way to copy/paste is to highlight the entire command with the mouse and then middle clicking to paste.

---

### Post by shadowlands on 2008-12-13
Awesome,:p):P problem fixed!!!> **drs305 said:**
> Let me make sure I understand you. When you run the 'gedit' command a file opens and this is what is in the file?
```

--19:26:47-- http://www.medibuntu.org/sources.list.d/hardy.list
=> `hardy.list.2'
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]
0K 100% 14.09 MB/s
19:26:48 (14.09 MB/s) - `hardy.list.2' saved [226/226]

```

Even if not, let's just recreate the medibuntu sources.list entry. We will rename that file for backup purposes and replace it by running the following commands:
```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bad
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get update
sudo apt-get upgrade

```

This assumes you are running Hardy Heron.
**Added**: In ubuntu, the easiest way to copy/paste is to highlight the entire command with the mouse and then middle clicking to paste.

---

### Post by shadowlands on 2008-12-13
The first command not work for me the directory could not be found.  The other Commands found errors saying information was old,or had been ignored.  I trusted the commands and soon after finding errors I was prompted to answer Y/n or y/N and I answered yes to all the prompts and the next thing I new the lil star was up on the computer indicating I could down load installations

---

