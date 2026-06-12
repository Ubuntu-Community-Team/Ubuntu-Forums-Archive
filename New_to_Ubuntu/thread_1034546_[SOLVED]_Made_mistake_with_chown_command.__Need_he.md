---
title: "[SOLVED] Made mistake with chown command.  Need help to fix."
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Kappity on 2009-01-08
I stupidly ran the following command while in the usr/bin directory "chown root:myusername *".  Yes, I'm sure it was a very dumb thing to do.  It was very late, and I was following some partially understood instructions to change the permissions on Google Earth (I had to type "sudo googleearth" in a terminal to start it).

Now every normal program still seems to be working fine, except that I have to do the following to start certain programs:

Google Earth only starts when I switch user to root (in the terminal) and then type: "sudo Googleearth"

Synaptic will no longer start from the menu (no error messages it just doesn't runJ).  I have to switch user to root in a terminal and then type "synaptic"

Update manage starts from the menu, but when I try to install updates, it just churns for a while and then does nothing.  I can switch user to root in a terminal, type "update-manager" and then install the updates from the program as I normally would.

Maybe other programs would have a problem and I just haven't discovered them yet.

I figured maybe if I did what I had done in reverse it would fix things, so I tried "chown myusername:root *".  No such luck.

I found this post, [http://tinyurl.com/7v43gj](http://tinyurl.com/7v43gj).  It mentions a hidden file .Xauthority which governs sudo permissions, but I don't seem to have any such file on my computer.  I set Nautilus to show hidden files, and searched for it.

So what I'd like to do is get back to the point where I can start these programs without doing what I described above.  I'm quite willing to listen to personal criticism about newbies who mess with stuff they don't understand, if I can also get a solution.:oops: :confused:

---

### Post by HermanAB on 2009-01-08
If that is actually what you did, then it is easy to reverse:
$ sudo chown root:root /usr/bin/*

Otherwise, you can re-install, since it only takes about 30 minutes - if that.

Cheers,

Herman

---

### Post by Kappity on 2009-01-08
> **HermanAB said:**
> If that is actually what you did, then it is easy to reverse:
$ sudo chown root:root /usr/bin/* 


Didn't work, alas.  I must have done something else that I don't remember.  This was a couple of days ago, and I wasn't really worrying about Google Earth so much.  It was when I tried to install some updates today that I discovered I'd messed other stuff up.

> **HermanAB said:**
> Otherwise, you can re-install, since it only takes about 30 minutes - if that.

Cheers,

Herman

Well, yes, but I'd rather learn to fix the problem without doing that.  I'll probably mess other things up in the future, and don't want to re-install each time.  ;)

---

### Post by MighMoS on 2009-01-08
Regarding the Synaptic issue, what happens if you run the following from a terminal (as a normal user)? ```
gksu synaptic
```

Are there any error messages then?

---

### Post by Kappity on 2009-01-08
> **MighMoS said:**
> Regarding the Synaptic issue, what happens if you run the following from a terminal (as a normal user)? ```
gksu synaptic
```

Are there any error messages then?

No, but the program doesn't start, either, except that I briefly see something on my bottom panel, which then goes away.

Also tried "sudo gksu synaptic" and get the suggestive message "sudo: must be setuid root"  So looks like I've somehow removed myself from the list of users that can use sudo, I could use it before.  Found manual pages on sudo and the sudoers file, and my brain locked up.  I'm going to step away from the computer and take this up in the morning.

---

### Post by albinootje on 2009-01-08
> **Kappity said:**
>  I figured maybe if I did what I had done in reverse it would fix things, so I tried "chown myusername:root *".  No such luck.

```

sudo chown -R 0:0 /usr/bin/ 

```
is good.
> 
I found this post, [http://tinyurl.com/7v43gj](http://tinyurl.com/7v43gj).  It mentions a hidden file .Xauthority which governs sudo permissions, but I don't seem to have any such file on my computer.

You really need it to have a Desktop Environment running.
Try :
```

ls -la ~/.Xauthority

```
Please do a :
```

sudo chown -R your_username:your_username /home/your_username

```
And see whether that helps
Please post the output of :
```

tail -f -n50 ~/.xsession-errors

```

---

### Post by albinootje on 2009-01-08
> **Kappity said:**
>  Also tried "sudo gksu synaptic" and get the suggestive message "sudo: must be setuid root"  So looks like I've somehow removed myself from the list of users that can use sudo, I could use it before.

"sudo gksu synaptic" is not what you want, and that error message is actually correct (I get it too on my machine), so don't worry about possible sudoers file problems.

You want this instead :
```

gksu synaptic

```

---

### Post by Kappity on 2009-01-09
> **albinootje said:**
> ```

sudo chown -R 0:0 /usr/bin/ 

```
is good.

First, thanks for taking the trouble to advise me.

If I try *any* sudo command while logged in as myself, I get the message "sudo: must be setuid root".  I know that sudo is supposed to let me use root privileges for one command, but it doesn't do it any more.  If I do an "su", and actually change to being root, then I can run the above command, and it takes it, but nothing has changed.


> You really need it to have a Desktop Environment running.
Try :
```

ls -la ~/.Xauthority

```

Okay, it's there.  My mistake.

> Please do a :
```

sudo chown -R your_username:your_username /home/your_username

```
And see whether that helps

Okay, tried it (again had to switch to root first, using su rather than sudo.  It took the command, but nothing appears to have changed.

> Please post the output of :
```

tail -f -n50 ~/.xsession-errors

```
OK.  Some of the following pretty clearly is not connected to the problem I'm writing about, but some of it I'm not sure about, so I left it all in.
```


SENDING COMMAND: exit
Bad UTF-8 in startup notification message
Bad UTF-8 in startup notification message
Bad UTF-8 in startup notification message
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3c00007 specified for 0x3c00005 (Initializi).

(4digits:7221): libglade-WARNING **: could not find glade file '/usr/games/4digits.glade'
VLC media player 0.8.6e Janus
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a000fc (VLC media )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
[00000290] main playlist: stopping playback
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4400005 specified for 0x440003d ().
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1231477200
evolution-alarm-notify-Message: alarm.c:246: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1231563600 1231477200
evolution-alarm-notify-Message:  Sat Jan 10 00:00:00 2009

evolution-alarm-notify-Message:  Fri Jan  9 00:00:00 2009

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)


```

Any useful clues there?

---

### Post by Kappity on 2009-01-09
> **albinootje said:**
> "sudo gksu synaptic" is not what you want, and that error message is actually correct (I get it too on my machine), so don't worry about possible sudoers file problems.

You want this instead :
```

gksu synaptic

```

Thanks.  Yes, I had tried ```
 gksu synaptic 
``` first.  On the panel at the bottom of the screen, I briefly get a tab that says "starting administrati . . .", then it disappears and nothing else happens.  I only tried it with the sudo after that had failed.

If I click on shortcut for synaptic in the system menu, then I get the same symptoms as above.

I've discovered that if I type just "synaptic" in the terminal, while signed in as myself, it gives me a message that it is starting the program without admin privileges, and that I won't be able to apply changes.  It does start the program then, however.

If I su to root, then I can type "synaptic", and start it up with user privileges.  Sudo won't work, though.

---

### Post by hyper_ch on 2009-01-09
the only real way to fix a "[recursive] chowned system directory" is to reinstall...

---

### Post by albinootje on 2009-01-09
> **Kappity said:**
>  If I try *any* sudo command while logged in as myself, I get the message "sudo: must be setuid root".  I know that sudo is supposed to let me use root privileges for one command, but it doesn't do it any more.  If I do an "su", and actually change to being root, then I can run the above command, and it takes it, but nothing has changed.


OK.
I just learned something new and very interesting here.
On my own machine I did the same yesterday, and now I couldn't use sudo anymore with the same error as you got.

A sudo chown -R root:root (0:0 is the same) is actually a very *bad* idea in case of the /usr/bin directory. :(

It makes the setuid flags disappear from the setuid binaries!

These are the correct permissions for sudo and sudoedit :
```

$ ls -la /usr/bin/sudo*
-rwsr-xr-x 2 root root 115136 2008-09-01 15:17 /usr/bin/sudo
-rwsr-xr-x 2 root root 115136 2008-09-01 15:17 /usr/bin/sudoedit

```

Can you run
```

su -
chmod u+s /usr/bin/sudo*

```
And then try "sudo some-command" again.

Sorry for the inconvenience.

---

### Post by Kappity on 2009-01-09
> **hyper_ch said:**
> the only real way to fix a "[recursive] chowned system directory" is to reinstall...

Ouch.  If that's the case, then that's what I'll have to do.  First, though, I'll continue using it this way for at least a few days, to see what else might not be working right, and see if other suggestions come up.  At least it looks like I can su to root when I need to do something that requires those privileges, and I can still run all my normal applications from the applications menu.

---

### Post by matey3 on 2009-01-09
I was wondering if you used -R with chown?
but you can always su or sudo or log in as root (gdm only) to fix your users rights.

---

### Post by MighMoS on 2009-01-09
albinootje is right, that will fix your sudo command (or should, you may have to do it from root as "recovery mode" when you boot). but there's no telling what *other* programs need their setuid bit set (ping is one, I know). I know the forum guidelines say reinstalling is a bad idea, but here it may be the only way. Other than maybe:
```
for i in /usr/bin/*;do dpkg -S $i;done|awk -F: '{print $1}'|uniq > REINSTALL_LIST.txt
apt-get install --reinstall `cat REINSTALL_LIST.txt`

```
The above code *should* scan /usr/bin for any files there, and see what package they belong to. Duplicates will be deleted from our list via uniq, and then each package which has something in /usr/bin will reinstalled. This should get your setuid bit back (although this meathod is pretty much like reinstalling).

---

### Post by Kappity on 2009-01-09
> **albinootje said:**
> OK.
I just learned something new and very interesting here.
On my own machine I did the same yesterday, and now I couldn't use sudo anymore with the same error as you got. [snip]

Can you run
```

su -
chmod u+s /usr/bin/sudo*

```
And then try "sudo some-command" again.

Sorry for the inconvenience.

I overlooked this post of yours until now.  The chmod command you give appears to have fixed everything, at least everything that I had noticed until this point.  I can run a sudo command to start Google Earth from my own account again.  Synaptic and the update manage both run from the menu shortcuts again.  Thanks much for your help.

---

