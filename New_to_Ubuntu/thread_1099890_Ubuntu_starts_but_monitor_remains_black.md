---
title: "Ubuntu starts but monitor remains black"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by emmwee on 2009-03-18
For "ideeological" reasons, I'm very happy that I substituted Windows with Linux, and I'm satisfied with my Ubuntu that can do all what Windows can do, and I even find it more userfriendly than Vista.
There are only 4 things I would like to resolve. I will post my 4 problems in 4 separated threads.

1st problem:
Ubuntu starts, but sometimes the monitor remains black (I hear the drums, I write - blind - my username and password, I hear the music ... but I don't see anything).
How can I shutdown or restart the system instead of power off drastically the pc? I mean: are there any short cuts like two times Alt+F4? Or Alt+??? for entering in the "System Menu", then "ALT+???" for the arrest command and so on? Or something like this that I can do "blind"?

---

### Post by Cypher on 2009-03-19
Once the monitor goes dark, does rebooting machine it work again?? To safely reboot your machine you can hit CLTR+ALT+F1 to get a text login prompt. Login and then run "sudo /sbin/reboot"..

---

### Post by emmwee on 2009-03-19
I tried at once if it works, but ... ?
With "CTRL+ALT+F1" I got at once to the prompt. I had to enter my "ubuntu log-in", but it didn't accept my username-password-combination I usually use to enter to ubuntu. What is the "ubuntu log-in"?
After 3 trials if got a message about these failure but I also got a new prompt "ubuntu @myusername". I wrote "sudo/sbin/reboot" but it told me that this directory doesn't exist. Then I wrote "exit" and I turned back to my desktop.
Maybe it's not the right way ...

---

### Post by anewguy on 2009-03-19
Well, first off there is a space between sudo and /sbin.  But let's take a little different approach:

type:

sudo shutdown -r now <press enter>

This tells the system (1) you want to shutdown the current run, (2) -r tells the system you want to reboot after the shutdown, and (3) now tells the system to do it immediately, killing all active processes (so if you did have a program running it's possible, though doubtful, you could lose data).  Remember there are spaces between each word and the -r as well.

Post back after you've tried either way.

Dave :)

---

### Post by emmwee on 2009-03-20
I tried what you said to me: this time - after digiting CTRL+ALT+F1 - everything was black, but here was no prompt blinking! I pressed "ALT+SysRq+B" and I wrote "exit" - but nothing happened ... and once again I powered off my pc brutally.
Now I found out a way what to do if Ubuntu will start with the music in the background (as I described in my thread) but the monitor remains black. For sure it's not very elegant, but maybe it's the safest way to turn out the pc:
1) "ALT+F1" (the focus goes on "Application" as the 1st menu point)
2) 2x "-> (arrow left)" (the focus goes on "System" as the 3rd menu point)
3) 8x "(arrow down)" (the focus goes on "Turn off")
4) "Enter"
5) "ALT+r" (as Italian "a**_r_**resto" = turn off)

---

