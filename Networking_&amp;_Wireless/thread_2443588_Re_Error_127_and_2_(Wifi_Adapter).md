---
title: "Re: Error 127 and 2 (Wifi Adapter)"
date: 2020-05-17
forum: Networking &amp; Wireless
---

### Post by jay56547 on 2020-05-17
I'm extremely new to Linux. I used Ubuntu 20.04 and I'm trying to install a wifi driver. Here is the link: [https://www.amazon.com/dp/B07QC3XQHW/ref=cm_sw_r_apa_i_42xWEb9NXVR9V](https://www.amazon.com/dp/B07QC3XQHW/ref=cm_sw_r_apa_i_42xWEb9NXVR9V) 
(Drivers are included on that page in the "about" area) 
I did install.sh and got 127 error and fixed that by using build-essentials but then got compile make driver error: 2. Did something with updating linux-headers- generic and that didn't work. Could someone please download the driver's and write a step by step instructions on how to install it?

---

### Post by CelticWarrior on 2020-05-17
Welcome.

One of the reviewers explained a much better method.

---

### Post by jay56547 on 2020-05-17
What do you mean? I just need a decent guide to set this thing up.

---

### Post by DuckHook on 2020-05-17
I believe that CelticWarrior is referring to this: [https://www.amazon.com/gp/customer-reviews/R2D0SQ7SODW80E/ref=cm_cr_dp_d_rvw_ttl?ie=UTF8&ASIN=B07QC3XQHW](https://www.amazon.com/gp/customer-reviews/R2D0SQ7SODW80E/ref=cm_cr_dp_d_rvw_ttl?ie=UTF8&ASIN=B07QC3XQHW) …but CelticWarrior can clarify if I am wrong.

On my Amazon page, it was the second review from the top.

---

### Post by jay56547 on 2020-05-17
I didn't see that, my bad.
I thought you had to use install.sh file to install it. 
 Also I don't understand how to do step 2...

---

### Post by DuckHook on 2020-05-17
> **jay56547 said:**
> …I don't understand how to do step 2...
I'm afraid you're in for a bit of an adventure:
[https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository)
…and:
[https://www.howtogeek.com/451360/how-to-clone-a-github-repository/](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/)
It's something of a learning curve, but I'm afraid there's no getting around the complexity. That's just how git works.

---

### Post by DuckHook on 2020-05-17
Anticipating your next question, a bit of web searching directs us to the following git repo: [https://github.com/brektrou/rtl8821CU](https://github.com/brektrou/rtl8821CU)

That's about as far as I can help you with this. It's a big minus when I have neither the WIFI dongle to work with nor the in-depth WIFI knowledge.

What I *can* do is move your thread to the Network and Wireless subforum where the network gurus are more likely to see it.

---

### Post by jay56547 on 2020-05-17
Uh. Confused. First, which link do I use for cloning, second, it doesn't look that hard to clone? That USB GitHub thing just says for the terminal to use "Git clone (url here)"
(Which I assume I'll need a temporary wifi connection to do)


Also that would be helpful

---

### Post by CelticWarrior on 2020-05-17
Yes, you need a temporary internet connection. But before going any further please post the relevant line that identifies the dongle by running 'lsusb' in terminal.

What I said about the reviewer with Git assumes the chipset inside is still the same as it was an year ago. Manufacturers tend to use different chipsets for the same model, different revisions.

---

### Post by DuckHook on 2020-05-17
The instructions were linked to in my second post. The actual repo that you wish to clone is in my third post.

If you read through the git site's help page, it explains in detail the process that you go through. How to find the link in the repo, how to start the cloning process, etc. It's seven steps of command line instructions. As said, it's a learning curve. Please read through the instructions before trying.

You will need a wired connection first. You must have access to the internet before you can clone the git repo. Since your WIFI is not yet working, you will have to bootstrap up to WIFI functionality by first making use of wired access.

---

### Post by jay56547 on 2020-05-17
> **DuckHook said:**
> The instructions were linked to in my second post. The actual repo that you wish to clone is in my third post.

If you read through the git site's help page, it explains in detail the process that you go through. How to find the link in the repo, how to start the cloning process, etc. It's seven steps of command line instructions. As said, it's a learning curve. Please read through the instructions before trying.

You will need a wired connection first. You must have access to the internet before you can clone the git repo. Since your WIFI is not yet working, you will have to bootstrap up to WIFI functionality by first making use of wired access.

So to get this straight, I can't use the readme instructions provided on that repo to clone that same repo?

---

### Post by DuckHook on 2020-05-17
> **jay56547 said:**
> So to get this straight, I can't use the readme instructions provided on that repo to clone that same repo?
I did not delve into the readme file in detail until just now. As mentioned, I have no reason to use this HW so it's a bit of the blind leading the blind. However, these instructions appear to be good ones, so please feel free to follow them.

Before diving in with both feet, please note CelticWarrior's latest post. It doesn't hurt to follow his instructions and ascertain that your chipset is, indeed, the one that you will be expending all of this time trying to install drivers for. OEMs do switch chipsets. It would be both frustrating and a waste of time to go through the trouble of compiling/installing drivers for a chipset that did not even exist.

---

### Post by jay56547 on 2020-05-17
Oh God, I didn't even notice, I only seen your post! I'll give them the ID when I have access to my computer later. Thank you for the help by the way.

---

### Post by jay56547 on 2020-05-17
I apologize I didn't see your message. I think I found it. The one called Realtek right? It's ID  0bda:c811

---

### Post by wildmanne39 on 2020-05-17
Chil555's directions here should get it working, they are the same that DH posted but with a little variation and easier to follow imo.

[https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp](https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp)

---

### Post by DuckHook on 2020-05-17
This ID confirms that your chipset is the one that the above driver is designed for. In subsequent searches, I also ran across a summary of the commands for solving your issue. Here is a link to our sister site with instructions from chili555: [https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp](https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp)

When it comes to networking and especially WIFI, it is always, *always*, ***always*** worth reading anything that chili writes. His answer is at the bottom of the thread and he has distilled the instructions down to a simple set of steps.

Good Luck and Happy Ubuntu-ing!

---

### Post by jay56547 on 2020-05-17
It works perfectly! Thank you! 

One thing. 1. I can't seem to open "Ubuntu Software" which I assume is the store. 
2. Can I install updates if I'm using an external hard drive that has persistence? (With Try Ubuntu option)

---

### Post by wildmanne39 on 2020-05-17
You should be able to install updates, try from the terminal:
```
sudo apt update && sudo apt upgrade
```
If you have any further trouble installing software please start a new thread with a descriptive title in the appropriate sub-forum because we only allow one issue per thread, please use thread tools at the top of the page to mark this thread solved.

Please note if you are running a dual boot system and you installed the bootloader to your external drive you will not be able to boot the OS that is on your internal drive if you unplug the external drive.

Thanks

---

### Post by DuckHook on 2020-05-17
You are running Ubuntu as a Persistent LiveUSB? That changes things. In addition to wildmanne39's reply please consider the following.

Ubuntu Software is what you call the "store", but you may wish to start thinking the Linux way and slowly recondition your habits to think of it as the repository. In many ways, Linux is the opposite of the proprietary space from which you have come. You may find it useful to read the link in my sig: *Linux is Not Windows*

I'm trying to read between the lines here, but I'm getting the impression that you are still in test-drive mode. If so, I would recommend the following:

[LIST=1]
[*]Use the LiveUSB session to get a general feeling for Ubuntu, but don't try to take it too far. If you like what you see, then instead of trying to install stuff into a LiveUSB,
[*]Install VirtualBox or VMWare on your current OS and then run Ubuntu properly within a VM. That way, you can get a real feeling for the OS.
[*]If you feel that you should go further and that a VM is too limiting for you, do further research at that time, ask for advice on these forums and consider a dual boot. There are good complete instructions on how to install dual boots on the Internet, but they must be current. Old instructions will cause you nothing but grief. At this time, I would not recommend a dual boot until you are really sure you like Ubuntu.
[/LIST]

---

### Post by jay56547 on 2020-05-17
I do enjoy Ubuntu, other than not understanding how things are installed with code. Plus I have to use this as it has better OpenGL support for AMD GPU's. I appreciate the help.

---

