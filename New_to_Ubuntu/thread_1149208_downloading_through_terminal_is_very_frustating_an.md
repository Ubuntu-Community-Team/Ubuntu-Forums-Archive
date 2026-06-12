---
title: "downloading through terminal is very frustating any other way around"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by brad_pitt on 2009-05-05
Hi All,

I recently installed ubuntu 8.10 on my machine.I typed this command in terminal 

```
$sudo apt-get install
```

It is taking ages to download it is happening because i have very slow internet connection(56 kbps).I was trying to execute this command since two hours and every time my internet connection is broken or connection lost and i have to start this process again.

I am looking for a method like download manager to do these kind of tasks rather than depending on terminal to download.

Please don't laugh about my internet connection.

Regards
Brad.

---

### Post by Jimmynemo2 on 2009-05-05
can we assume you had a program to install after that command?

$sudo apt-get install wouldnt actually install anything, sicne the command requires a program after that to install.

Aslo, click your applications menu, then add-remove programs for a gui version of this tool (though apt-get command line is faster when you know what you want to install)

hope this helps...

---

### Post by stumbleUpon on 2009-05-05
If you dont like the terminal try using synaptic ([https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)). The basic process is still the same, i.e., apt.

Even in the terminal what are you trying to install?

The command is usually 'sudo apt-get install somePackageName'. But you havent specified what package you want to install.


EDIT: Late by a few seconds...!!!

---

### Post by inyoka on 2009-05-05
If its just the odd big file you can use wget, I live in Indonesia and we have similar problems.  Synaptic resumes but apt-get doesn't, don't know why.

Anyway when your download fails copy the files location from the terminal e.g :
"http://packages.medibuntu.org jaunty/non-free w32codecs 20071007-0medibuntu4"

then run ...
```
wget http://packages.medibuntu.org jaunty/non-free w32codecs 20071007-0medibuntu4

```

..but with the file you want. For help use :
man wget

Here's a quote from the manpage "Wget has been designed for robustness over slow or unstable network connections"  

I'm sure theres a more elegant solution but thats what I do. Good luck.

---

### Post by Funnnny on 2009-05-05
I think he knows how to use that command, but the downloading is so long because of his connection.
So if you want to download, and resumable when downloading, get to getdeb.net, you may find yours app, or just copy the downloading in the terminal and use another download manager ( DownThemAll is a good try )

---

### Post by lavinog on 2009-05-05
Brad, welcome to Ubuntu.

Why are you using the terminal? Are you following a guide?
Most packages in the repository are reasonably small, with exception to some proprietary packages, and data files for games...etc.

Are you in the US?  Many broadband providers offer packages that are cheaper than dialup when you factor in the cost of the 2nd phone line.

I had to live with my Dad for a couple of months, and he was using dial-up and the phone line quality was so bad that he couldn't stay connected for more than 10 mins. It was impossible to update his virus definitions online. It turned out that the phone pedistal by his house was filled with ants. Shortly after they replaced the pedistal, the county road maintenance crew ripped up the new phone lines.

---

### Post by misfitpierce on 2009-05-05
Not of help but wow... I didnt know anyone still used dial-up, If in the US then what lavinog said is very true :)

---

### Post by Funnnny on 2009-05-05
[COLOR=Teal]**~> Afaik, in my country still have some people using dial-up, not much but they're using...**[/COLOR]

---

### Post by Sarai the Geek on 2009-05-05
> **Funnnny said:**
> [COLOR=Teal]**~> Afaik, in my country still have some people using dial-up, not much but they're using...**[/COLOR]

Lots of people in Alaska have dial-up. Out in the bush they mostly have high speed (comes in via satellite and a wifi signal or two reaches the entire town) but some of the suburbia-type places outside urban areas don't necessarily have cables run in. Last fall I lived in a house that only had dial-up: yuck. I ended up using someone down the street's internet- raise a glass for all the people out there running unsecured networks called "linksys." :)

---

