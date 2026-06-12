---
title: "firefox 1.5.0.9 and yahoo mail crashing"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by rejean on 2007-01-12
Hi all! I installed  Ubuntu 6.06 a few weeks ago and I had no problems with Firefox 1.5.0.9. I did all the updates on a daily basis. 
I use the yahho.ca portal as my default home page. Until this morning I could open my email or compose a new message but now whenever I try to do so Firefox closes without any notice. I have rebooted into Ubuntu a few times hoping it would cure the problem. What do you think happened? What can I do? Any suggestion will be greatly appreciated.

---

### Post by stupidkid on 2007-01-12
Can you run firefox from terminal and post all the output?

---

### Post by rejean on 2007-01-12
Hi stupidkid!
How would I do that? Here is what I tried;

```

rejean@rejean-desktop:~$ ./firefox
bash: ./firefox: No such file or directory
rejean@rejean-desktop:~$ run /home/rejean/mozilla/firefox
bash: run: command not found
rejean@rejean-desktop:~$ ./mozilla/firefox
bash: ./mozilla/firefox: No such file or directory
rejean@rejean-desktop:~$ cd /home/rejean/mozilla/
bash: cd: /home/rejean/mozilla/: No such file or directory
rejean@rejean-desktop:~$ ls
Desktop  Examples  Incomplete  key.gpg.asc  Shared
rejean@rejean-desktop:~$ cd
rejean@rejean-desktop:~$ cd /home
rejean@rejean-desktop:/home$ ls
rejean
rejean@rejean-desktop:/home$ cd /rejean
bash: cd: /rejean: No such file or directory
rejean@rejean-desktop:/home$ cd rejean/
rejean@rejean-desktop:~$


```

---

### Post by stupidkid on 2007-01-12
$ firefox

don't use the "./firefox" just "firefox"

---

### Post by rejean on 2007-01-12
ok! Gotcha! Here it is, no message, just a new firefox window opened.
```

rejean@rejean-desktop:~$ firefox
rejean@rejean-desktop:~$


```
I have no problem running FF.
I've been using it to post here and reply. The only problem is when I click on email or compose mail from the Yahoo.ca portal

---

### Post by stupidkid on 2007-01-12
Yes exactly, run firefox and then make it crash. Post the output in the terminal.

---

### Post by rejean on 2007-01-12
Ok!
It could have been that I had tried opening FF in a terminal while I had one running already. So I closed all FF and open it from the console then I crashed it clicking on Compose Mail and here is what I got:

```

rejean@rejean-desktop:~$ firefox
*** CLB *** Initializing Google Browser Sync...
*** CLB *** Instanciating core objects...
*** CLB *** Registering with XPCOM...
*** CLB *** Adding categories...
*** CLB *** Google Browser Sync initialized succesfully!
Segmentation fault
rejean@rejean-desktop:~$


```

so the last line ( I mean second last line, obviously, is the result of the crash ).

---

### Post by mtierney on 2007-01-12
Would it be wise to diagnose the problem by downloading the Firefox debug symbols and running
```
$ firefox -g
```
... sort of like a verbose firefox but with gdb doing the work?

(of course, this might make things more complicated since we have to run through gdb...)

new to debugging firefox problems,
mtierney

---

### Post by rejean on 2007-01-12
I have no clue about the firefox debug symbols. Where would I get them. I went however into Synaptic and I do have gdb installed so I tried this;

```

rejean@rejean-desktop:~$ firefox -g
GNU gdb 6.4-debian
Copyright 2005 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

```

which I tried and got;
```

(gdb) show warranty
                        NO WARRANTY

  11. BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY
FOR THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE LAW.  EXCEPT WHEN
OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES
PROVIDE THE PROGRAM "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED
OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.  THE ENTIRE RISK AS
TO THE QUALITY AND PERFORMANCE OF THE PROGRAM IS WITH YOU.  SHOULD THE
PROGRAM PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL NECESSARY SERVICING,
REPAIR OR CORRECTION.

  12. IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING
WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR
REDISTRIBUTE THE PROGRAM AS PERMITTED ABOVE, BE LIABLE TO YOU FOR DAMAGES,
INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING
OUT OF THE USE OR INABILITY TO USE THE PROGRAM (INCLUDING BUT NOT LIMITED
TO LOSS OF DATA OR DATA BEING RENDERED INACCURATE OR LOSSES SUSTAINED BY
YOU OR THIRD PARTIES OR A FAILURE OF THE PROGRAM TO OPERATE WITH ANY OTHER
PROGRAMS), EVEN IF SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE
POSSIBILITY OF SUCH DAMAGES.

(gdb)

```

Any suggestion?

---

### Post by hopestorm on 2007-01-12
Sounds like I got the same problem.

But not yahoo email, it crashes just too often. I am a little bit scared of Ubuntu already, since it's not a problem for firefox in Windows.

---

### Post by rejean on 2007-01-12
Yes! No problem in XP ( although I have FF 2.0 ) or Debian ( should check the version. I can also check PCLinuxOS and Sabayon but I think they also have FF 2.0. ) and it was working fine in Ubuntu until last night. It has to do with some new updates.

---

### Post by bburgin on 2007-01-24
I'm having the same problem using Firefox with Yahoo mail.  All the other sites I visit do not cause Firefox to shut down inadvertently, just when logging into the mail client. My yahoo homepage will load however.  Do you suppose there is a problem with the new Yahoo Mail Beta client I'm trying to login to with version 1.5.0.9 of Firefox?

BBurgin

---

### Post by bburgin on 2007-01-24
Its definitely Yahoo's problem.  I logged into Yahoo using Internet Explorer on my Ubuntu machine, and instead of IE closing like Firefox I got a web page that tells me the new YAHOO mail doesn't support the operating system I'm using.  It did give me the option to switch back to the old Yahoo mail. I did select the old Yahoo mail client and tried again, however it still shutdown.  maybe need to clean cache and cookies?  Suggestions now?

BBurgin

---

