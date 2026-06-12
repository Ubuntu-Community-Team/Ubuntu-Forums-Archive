---
title: "Other Ubuntu 11.04 Questions"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-29
It's me again. ^^;; I have a couple of questions regarding this new release of Ubuntu.

1. I finally got grub working and can see the OS to choose from at startup. But when I choose to load Ubuntu, there is no loading screen, just a purple screen that lasts until the login screen. Is there any way to get the loading screen or does this new version have one? **[SOLVED!]**

2. I also noticed in the grub loader that it mentions previous Linux installations (or something like that). Does that mean that the previous version of Ubuntu is still on the computer, available for bootup? Is there any way to take that off or should I just ignore it? ;P **[SOLVED!]**

3. I'm actually not liking the new interface too much, how can I switch back to the classic Ubuntu look (I'm not sure where to select that option)? **[SOLVED!]**

4. When I was updating Ubuntu from 10.10 to 11.04, this message came up: "Third party entries in sources list were disabled. Re-enable them with 'software-properties' tool or your package manager." Where can I find the package manager, or how do I access software-properties?

Thank you! :)

---

### Post by Hedgehog1 on 2011-04-29
Answer to question #3: You can Run Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by unknowngal on 2011-04-29
> **Hedgehog1 said:**
> Answer to question #3: You can Run Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

Thank you! That worked! :)

*hopes the other questions can be answered, maybe* :3

---

### Post by unknowngal on 2011-04-29
Just bumping up the thread. Sorry! ^^;;

---

### Post by unknowngal on 2011-04-29
Anybody have any ideas or comments regarding my other questions? Thank you! XD

---

### Post by sandyd on 2011-04-29
> **unknowngal said:**
> It's me again. ^^;; I have a couple of questions regarding this new release of Ubuntu.

1. I finally got grub working and can see the OS to choose from at startup. But when I choose to load Ubuntu, there is no loading screen, just a purple screen that lasts until the login screen. Is there any way to get the loading screen or does this new version have one?
**Have you installed the nvidia/ati propreity drivers? If yes, that purple screen is normal**
2. I also noticed in the grub loader that it mentions previous Linux installations (or something like that). Does that mean that the previous version of Ubuntu is still on the computer, available for bootup? Is there any way to take that off or should I just ignore it? ;P
**Nope. their just older kernels of ubuntu. Use computer janitor to remove it if you like!**
3. I'm actually not liking the new interface too much, how can I switch back to the classic Ubuntu look (I'm not sure where to select that option)? **[SOLVED!]**

4. When I was updating Ubuntu from 10.10 to 11.04, this message came up: "Third party entries in sources list were disabled. Re-enable them with 'software-properties' tool or your package manager." Where can I find the package manager, or how do I access software-properties?

Thank you! :)
.

---

### Post by unknowngal on 2011-04-29
Thanks very much for your replies! :) 

Regarding my first question, I went to check "Additional Drivers", and it says the Nvidia drivers are activated but not currently in use. I wasn't sure what to do next, so I decided to go to Google and search for "loading screen in Ubuntu 11.04" and came across this page:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Boot up splash screen issues for users of Ubuntu 10.04 & higher](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Boot up splash screen issues for users of Ubuntu 10.04 & higher)

I had already installed StartUp-Manager yesterday via the Ubuntu Software Center, but wasn't sure what to do either regarding it, until I found the above website. I just followed the instructions as close as possible (setting under the "Boot Options" tab the resolution as 1024x768, same in the "Advanced" tab), closed the window, and restarted the computer, and the Ubuntu logo appeared. :) For some reason, grub showed up smaller at startup, but that's okay.

About your answer to my second question, I'll give it a shot, though I've heard that computer janitor can affect things quite a bit? I'll try anyway. *crosses fingers* XD;

Thank you again! :)

---

### Post by Miljet on 2011-04-29
I'm not too fond of computer janitor. You can remove older kernels with synaptic package manager (which should help with your question 4). Just be sure you know which version you are currently using and don't remove that.

---

### Post by unknowngal on 2011-04-30
Thank you for your replies, guys! But now that I've moved to Linux Mint (at least for the time being :P), I should probably close this thread. I much appreciate the time you spent in replying though. :D

---

