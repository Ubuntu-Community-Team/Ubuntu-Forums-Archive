---
title: "cannot update or uninstall"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by donny.davis on 2011-07-20
hey i cant open the ubuntu software center or the synaptic package manager... also cant update 
eg. sudo apt-get update
its giving me the same error as mentioned below
i even tried removing google chrome... but again the same error



```
donny@donny-desktop:~$ sudo apt-get remove Google Chrome
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
donny@donny-desktop:~$ 
```

---

### Post by garvinrick4 on 2011-07-20
Open a terminal and:
```
sudo rm /var/lib/apt/lists/* -vf 
```
```
sudo apt-get clean all 
```
```
sudo apt-get update
```
Hopefully that fixed your problem:

---

### Post by donny.davis on 2011-07-20
hey thankz it worked

---

### Post by garvinrick4 on 2011-07-20
You are welcome Donny Davis from Mumbai. Enjoy your Ubuntu.

---

### Post by pinnodyr on 2011-07-21
Hey,

I have this same problem and been using the solution for a while (found it on another forum), but it seems like I have to do:

```
sudo rm /var/lib/apt/lists/* -vf
```

every single time when the update manager runs. It's a bit annoying :confused:

Any idea, what to do to solve this problem for good?

I was thinking about putting the command inside of cron and just set it to run every few hours, but there must be a solution to this problem instead of just deleting the entries every time.

---

### Post by garvinrick4 on 2011-07-21
Post results with error when updating from command line.

---

### Post by pinnodyr on 2011-07-25
Hi garvinrick4 and thanks for quick reply ;)

Apparently it seems that my problem has gone away.

I think I might have forgotten to do a ```
sudo apt-get clean all
``` and may have done a ```
sudo apt-get clean
``` which probably doesn't do anything at all :O

I'll post back if the problem persists ;)

---

### Post by donny.davis on 2011-07-26
hey i again got the same problem... its repeating
what to do ??????

---

