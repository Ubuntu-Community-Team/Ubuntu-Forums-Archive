---
title: "Online class uses windows. Help"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by Pearsonl on 2009-12-24
I have ubuntu and have just started a online school. The school uses windows and some of my assignments I can't do because of this. Any ideas?

---

### Post by danastasio on 2009-12-24
What exactly is the issue? I attend online classes at NECB where they say that you cannot use Linux with the online system and I used it all last semester without any problems. You have to say exactly what is wrong. If it simply them telling you that you have an unsupported operating system and they will not let you log in. Then there really isn't much that you can do about it unless you can somehow force the IT guy to let you log in. But without telling us what your problems are, we cannot give you an answer.

or rather we can...


42

now whats your question.

---

### Post by howefield on 2009-12-24
Do you have a windows disk ?

You could virtualise or dual boot.

Maybe run some windows programs through Wine.

What software do you need to run ?

---

### Post by alancop on 2009-12-24
Install the program called WINE. This will allow you to run windows programs on Ubunutu, by right-clicking on the .EXE and selecting open with WINE.

---

### Post by djchandler on 2009-12-24
> **Pearsonl said:**
> I have ubuntu and have just started a online school. The school uses windows and some of my assignments I can't do because of this. Any ideas?

There's a plug-in for Firefox called *User Agent Switcher* that lets you spoof the OS and browser both. If they are using the artifice of using the browser id string to avoid supporting Linux users, you may want to try using this plug-in and id your OS as WindowsXP and and browser as Internet Explorer 6.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Unless they use Windows specific executables, you may be able to work around this problem.

Just out of curiosity, what online school are you taking courses from? Do they support Mac OS X? If they support OS X and multiple browsers, Safari, Opera, Firefox, Chrome. etc., you're being fed a load of fertilizer.

---

### Post by Zzl1xndd on 2009-12-24
> **djchandler said:**
> 

Unless they use Windows specific executables, you may be able to work around this problem.

Just out of curiosity, what online school are you taking courses from? Do they support Mac OS X? If they support OS X and multiple browsers, Safari, Opera, Firefox, Chrome. etc., you're being fed a load of fertilizer.

I would look into this, I work for an E-learning company and I know most of our products have Linux support. Also most of our (and Competitors) courseware is Java and Flash based.

IF you can provided the School or the URL (if being accessed from a website) I might be able to provided some insight.

---

### Post by Garyhans on 2009-12-24
Try IE4Linux

[http://www.rapidsharemegaupload.com/ubuntu-ie4linux-crack-serial-keygen-free-download.htm](http://www.rapidsharemegaupload.com/ubuntu-ie4linux-crack-serial-keygen-free-download.htm)

---

### Post by Geoff918 on 2009-12-24
> **Garyhans said:**
> Try IE4Linux

[http://www.rapidsharemegaupload.com/ubuntu-ie4linux-crack-serial-keygen-free-download.htm](http://www.rapidsharemegaupload.com/ubuntu-ie4linux-crack-serial-keygen-free-download.htm)

Meh. Get winetricks and install IE7. It's so easy it's sick. And, you're not stuck with IE6 (which winetricks can also setup).

Install Wine from WineHQ repo and then get Winetricks installed. Done.

---

### Post by Dark_Stang on 2009-12-24
Be more specific with the issues you're having. The only class I had consistent issues with online was Discrete Math because the symbols never rendered correctly in any web browser on Linux.

---

### Post by oldsoundguy on 2009-12-24
Have had the same issue .. but I have always kept a Windows box in the corner.  Makes that that on line training in Adobe easy.  About the only time they go on line is to go to school.

You can get along fine on most school sites with a moderate speed single core P IV as long as you have a good sized drive and max out your memory.  SO, pick up a used one from Craig's list or your local Flea Market paper.

no hassle with the slowness of running Windows from a VM
Being able to instantly use your Linux box for research.

To make it REALLY easy run both computers through a KVM (use the same keyboard/video/mouse). 
You will be surprised just how easy it is!!

---

### Post by cartisdm on 2009-12-25
While in school I've always kept a dual-boot on my main computer.  I know there are ways to get like 90% of software running in linux but when its for school you're often on a deadline and don't have time to mess with bugs or learning curves.  A dual boot setup that has just the software loaded for school is a great idea, then after the time crunch is over, load it up in Ubuntu and spend some time figuring it out there!

Also, try running your online class in linux anyway.  A lot of time they post system requirements that are a load of horse crap

---

### Post by stalkier on 2009-12-25
> **cartisdm said:**
> Also, try running your online class in linux anyway.  A lot of time they post system requirements that are a load of horse crap

Agreed. I attended Kaplan University online for 5.5 years and have used Linux for the last 3 years. I have never had any issues with the school's online interface. Assignments were done in OpenOffice and submitted as .doc files etc. Firefox is a great browser and will work on the interface also for the school.  

Do not waste the time or money for M$ products if a better, safer alternative can be used.

---

### Post by djchandler on 2009-12-25
> **djchandler said:**
> 
Unless they use Windows specific executables, you may be able to work around this problem.
...
If they support OS X and multiple browsers, Safari, Opera, Firefox, Chrome. etc., you're being fed a load of fertilizer.

Another alternative is to use the hardware virtualization feature (Intel VT or AMD-V) built into newer x86 CPUs and run a virtual machine. There's qemu-kvm which is built into the kernel. The only way to get closer to running on bare metal is to boot Windows natively. It's possible to get 95-97% of the speed you get when running Windows alone. Of course this means you need a legal copy of Windows.

To discover whether or not your CPU supports hardware virtualization, open a terminal window and run cpuid. If your CPU does, you'll find the phrase *"Virtual Mode Extensions"* in the output.

To get started using virtualization, you may want to look at this thread:
[http://ubuntuforums.org/showthread.php?t=582729](http://ubuntuforums.org/showthread.php?t=582729)
Also, check on this:
[http://virt.kernelnewbies.org/TechComparison](http://virt.kernelnewbies.org/TechComparison)

I'm a fan of [VirtualBox (Sun Microsystems)]("http://www.sun.com/software/products/virtualbox/") myself. I believe their software must be accessing the kernel virtualization routines in order to get the speed they do. It's also very easy to set up your virtual machines with VirtualBox. There's a slightly older version in the Ubuntu repositories than what you can download directly from Sun.

Your school is trying to avoid support issues. That's just laziness besides being discriminatory in my opinion. Run Linux and get on with your studies.
:guitar:

---

### Post by danastasio on 2009-12-25
Look, there are alot of people here suggesting that you install WINE or IE4Linux. Which is all fine and well, but they are suggesting that you install things without knowing the problem, and im willing to bet that neither WINE or IE4Linux will help you at all. Either the website uses windows executables, and your only option is virtualization or a windows based machine, or they do not, and it will work just fine in linux. Please tell us exactly what your are having issues with so that we may better help you and not throw out totally random suggestions.

---

