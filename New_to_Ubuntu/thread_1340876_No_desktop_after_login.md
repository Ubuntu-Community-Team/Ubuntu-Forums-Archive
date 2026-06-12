---
title: "No desktop after login"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by jezebel on 2009-11-29
I just did some updates on my desktop Ubuntu (Karmic), and also changed the wallpaper...

On reboot, after the login screen, I just see the wallpaper and my arrow/cursor - but no icons, no menu access. 

Help please - is there any way I can rescue my ubuntu?

---

### Post by jrrader on 2009-11-29
It shouldn't be too difficult to fix this.  I wonder if maybe your home folder permissions were changed.  Edit: NVM, I see you have a log in screen.  Dumb on my part.  Just a moment.

---

### Post by BioVirtual on 2009-11-29
Try this:

1- hit ctrl-alt-F1 to move down to tty1.  Login with your username and password.
2-  			 				sudo apt-get  --reinstall ubuntu-desktop
3- sudo apt-get update

---

### Post by jrrader on 2009-11-29
From your login screen select xterm as your session (or do what the guy above me said, ctrl+alt+f1) then type this:

```
cd /home
ls -l
```
(that's an L not a 1)
This will list the names of the directories in your home folder. It should look something like this:
```
drwxr-xr-x 41 hyejin hyejin  4096 2009-11-26 09:54 hyejin
drwx------ 97 jeff   jeff    4096 2009-11-28 23:58 jeff

```

If it looks like this:
```
d--------- 41 hyejin hyejin  4096 2009-11-26 09:54 hyejin
```
(the part after the d, no r, w, or x)

or 
```
drwx------ 97 root   root    4096 2009-11-28 23:58 jeff
```
(jeff has changed to root)
we are having a permission or ownership problem.  Let me know.

---

### Post by jezebel on 2009-11-29
Hi and thanks for all the help -

Jr

Yes, I do have a login screen and prompt for password. I am the only user.

I will try the tactics suggested shortly - I'm off to cook dinner now... I will implement the solutions and report back and whether indeed solutions they were:-)

---

### Post by jezebel on 2009-11-29
Jrrader 

I did what you said, and it looks normal (as your first example). so no permissions problem.

Next step - should I try to reinstall desktop as suggested above?

---

### Post by jrrader on 2009-11-29
I went to bed, sorry for the late reply.  Yeah, you can try to reinstall gnome - won't hurt anything even if it isn't the problem - but before you do that maybe try adding a new user and logging in and seeing if the new user is able to log in properly.

ctrl+alt+f1 again
```
sudo adduser username
```
(change username to the name you want to log in with)

If you can log in with the new user then the problem is restricted to your home folder.  If not, then the problem is with gnome.  

Have you tried selecting fail-safe gnome from the session menu at the login screen?

---

### Post by BioVirtual on 2009-11-29
Let us know the result.

---

### Post by jezebel on 2009-11-29
No luck guys.

I created a new user, but had the same problem.

BioVirtual - I tried your advice, but the command sudo apt-get --reinstall ubuntu-desktop  resulted in the message that ubuntu-desktop was invalid

I then accidentally retyped install ubuntu desktop and that did something - but did not fix the problem. Only now my dual-monitors are back to the default being on the left (I'd changed that).

I don't care about losing data etc since I only ever play with Ubuntu and haven't stored anything there.

Any other help would be appreciated because if I can avoid a complete re-install that would be great as I'm always nervous about overwriting my main OS (vista)...

EDIT - I tried to reinstall gnome panels following the instructions on this thread here [http://ubuntuforums.org/showthread.php?t=881301](http://ubuntuforums.org/showthread.php?t=881301)

but still no luck...

---

### Post by jrrader on 2009-11-29
I think it should have been "sudo apt-get --reinstall install ubuntu-desktop"

I could suggest a few more things (install kubuntu-desktop...), but I don't think they'd be any more help than what I've already suggested.  Hopefully someone with a clue will come along.

---

### Post by jezebel on 2009-11-30
Thanks I tried reinstall, and still no good...

---

