---
title: "google earth install  terminal problem"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2009-05-18
I ran this "chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin"  now I can run terminal but synaptic says this:E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
  , is there anyway to undo this.

---

### Post by MeTylerDurden on 2009-05-18
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. (thats what I get when I run termial.

---

### Post by jespdj on 2009-05-18
So, did you do what it tells you to do?
> ... you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by MeTylerDurden on 2009-05-18
I got it working again... thanks anyhoo

---

### Post by MeTylerDurden on 2009-05-18
i ran it and restarted  , still had problem . then ran it again.. finally.. just took an awful long time to fix itself.. thanks for the reply.

---

### Post by 3rdalbum on 2009-05-18
Running the "chmod" command would not cause this error message to occur. It has occurred because of something else that happened.

If "sudo dpkg --configure -a" doesn't help the situation, you should tell us what you were doing that involved the package manager (apt-get, Synaptic, or dpkg programs) and we might be able to get things working again for you.

---

### Post by MeTylerDurden on 2009-05-18
This is the problem: seems I don't know how to accept this agreement

---

### Post by tarps87 on 2009-05-18
Press <Tab> then <enter>

Hope this helps

---

### Post by MeTylerDurden on 2009-05-18
Then this

---

### Post by tarps87 on 2009-05-18
That shouldn't happen, make sure the console is selected, if it still doesn't work try the right and lest arrows. In the console I use it is tab but I can vary.

---

### Post by MeTylerDurden on 2009-05-18
how do I show process running in terminal? -so I can try tab , enter..

---

### Post by tarps87 on 2009-05-18
Top will show you the main processes running, just type top into a terminal. In the window you are using the scrollbar is highlighted red, this means it is selected, tab or the directional keys will move the highlight to the OK button then you can press enter to select OK

---

### Post by MeTylerDurden on 2009-05-18
I ran top , but don't see anything there I understand.

---

### Post by tarps87 on 2009-05-18
That will be a list of processes, I think this is getting over complicated.
Click in the terminal and press the direction buttons or tab until the selector moves, then hit enter when the ok button is highlighted. I tried to recreate it with google earth but the latest version uses a GUI. Installing Java which has the same style selection pressing the tab selects the ok button.
It is really easier than we are making it ;)

---

### Post by MeTylerDurden on 2009-05-18
all good now thanks a heap, i ran "sudo dpkg --configure -a"  3 times and got the google earth agreement to appear. Used tab-enter to select ok at bottom of agreement. I'm back , many thanks

---

