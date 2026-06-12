---
title: "[SOLVED] desktop freezes when kopete loads but mouse pointer ok"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Chris Watts on 2008-12-12
[COLOR="black"][/COLOR]I recently loaded KDE as my default desktop to see if it was any more user friendly than gnome for a windows user. I can log in but the desktop appears and then kopete loads and the bouncing KDE logo part of the pointer lock and all screen freezes etc for mouse. there is still a little disk activity after this and my pointer still moves. I have a feeling that kopete is getting upset about not having a network connection perhaps. Anyway I wait until disk activity ceases and then close the laptop lid to suspend the machine - when I reopen the lid  KDE comes back from its frozen state without any borders around windows and all windows load in the top left corner of the screen. I can then do editing, write in this forum etc. Does anyone have any idea what this is actually caused by... and what conf file would I remove kopete's auto start from as I can't find any "start with OS" option in its setup window tabs. Thank you for your time.

---

### Post by Chris Watts on 2008-12-12
After googling this problem i found that kopete has a history of this sort of activity.... I wish Trillian had a linux version... oh well.
I can see Kopete at the bottom of the screen but it won't maximise or change desktop so that I can access it.... a kill-l gives me the following:

 1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL
 5) SIGTRAP      6) SIGABRT      7) SIGBUS       8) SIGFPE
 9) SIGKILL     10) SIGUSR1     11) SIGSEGV     12) SIGUSR2
13) SIGPIPE     14) SIGALRM     15) SIGTERM     16) SIGSTKFLT
17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
21) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU
25) SIGXFSZ     26) SIGVTALRM   27) SIGPROF     28) SIGWINCH
29) SIGIO       30) SIGPWR      31) SIGSYS      34) SIGRTMIN
35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3  38) SIGRTMIN+4
39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
43) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12
47) SIGRTMIN+13 48) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14
51) SIGRTMAX-13 52) SIGRTMAX-12 53) SIGRTMAX-11 54) SIGRTMAX-10
55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7  58) SIGRTMAX-6
59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
63) SIGRTMAX-1  64) SIGRTMAX


Which process is it?

---

### Post by Chris Watts on 2008-12-12
I give up - i am taking the advice of the fellow in the forum from yesterday and going back to XP. I  don't understand why you can't have a gui version of kill like windows has. and I can't understand why the processes and apps are all bundled in together and aren't listed by their actual name. It was very annoying to find that, when I had a party at my place last night, my mp3's couldn't be played because the laptop just froze on the KDE screen. You can say what you like about how linux is a wonderful server OS but as a desktop system I have never in my life seen something take so much time to set up and have so many problems. I know most of you spend your life in front of computers and that is probably why you can afford to use this OS, It has been 8 years since I used linux - maybe I'll check back in another 8 to see if you have gotten anything working except for the pretty vista looking gui that needs constant repairs. I have a life... now I am going back to it.... please delete my username from the Ubuntu forum database.

---

### Post by NoBugs! on 2009-01-06
Can you Ctrl+Alt+Escape and click the frozen application to stop it?
If that doesn't work, you could try either the system manager or command line to end process.

---

