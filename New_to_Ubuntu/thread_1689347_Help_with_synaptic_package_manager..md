---
title: "Help with synaptic package manager."
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Alan5901 on 2011-02-16
I am experiencing a problem with the Ubuntu software center. When ever I try to install or uninstall something it takes a very long time and then nothing happens. I thought that it is a result of a package that is incorrectly installed. When I try to go in to the synaptic package manager  I get this error message  E:dpkg was interrupted you must manually run sudo dpkg - configure -a to correct the problem. E:cache ->open()failed, please report.  From the message I thought that I could type sodo dpkg -- configure -a into the terminal and that this would resolve the problem. When I do this I am asked for my password I thought that this would be the one that I enter to log in on my computer but when I try to enter it nothing happens. Any help would be very much appreciated.
Thanks 
Alan

---

### Post by coffeecat on 2011-02-16
> **Alan5901 said:**
> From the message I thought that I could type sodo dpkg -- configure -a into the terminal and that this would resolve the problem.

It's 's[COLOR=Red]u[/COLOR]do dpkg --configure -a'. And there's no space between -- and configure. Check for  typos when using the terminal.

> **Alan5901 said:**
>  When I do this I am asked for my password I  thought that this would be the one that I enter to log in on my computer  but when I try to enter it nothing happens.

Use your login password, but in the terminal you get no visual feedback  when you type the password in. Don't worry - it is going in. Just type  it in and press ENTER.

---

### Post by sikander3786 on 2011-02-16
And if *sudo dpkg --configure -a* returns some errors, please post the complete output here for further assistance.

---

