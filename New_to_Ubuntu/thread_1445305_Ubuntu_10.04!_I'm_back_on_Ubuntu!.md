---
title: "Ubuntu 10.04! I'm back on Ubuntu!"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by falonyn on 2010-04-02
OK, so I recently switched back to Ubuntu on my laptop after running Windows 7 for a while and just not getting the performance I wanted from my OS. So I am loving Ubuntu, as I always have while running it, but I am having a couple issues that I just find unacceptable from a mature OS like Ubuntu.

1. DVD playback - Alright, so this could simply be my fault for not activating it correctly, but one DVD I have tried works, just none of the rest. How does one DVD work and the rest just not? I have used movie player and VLC. Nothing. 

2. Battery Life!!! How is this something that hasn't been fixed in all the iterations of Ubuntu since it started? I admit that I am almost always near an outlet, but really? This site touts how it is great for laptops, and it is other than this problem. And I KNOW that it doesn't affect all laptops, but it used to not affect any, and now it affects mine and has since 7. 

Talking with a Linux aficionado friend of mine says he looked into it and it is something in the kernel. But if this is the case, why has it not been fixed?

Anyway, I am just harping on the couple flaws that I have noticed, besides the issues I am having with ubuntu 10 beta because it is a beta and not complete. So understandable. Overall I WAY prefer Ubuntu on my laptop and don't plan on changing again. Everything is working well otherwise and for what I can and want to do on my laptop Ubuntu is better. (I can't play games on it so I don't need Windows)

Thank you Canonical for a great OS! Please fix the battery issue. It never used to be a problem.

---

### Post by Temposs on 2010-04-02
Regarding the DVD playing: have you installed the package called ubuntu-restricted-extras? That should enable dvd playing in addition to a number of other non-free media things.

---

### Post by gabak on 2010-04-02
the way i solve all my problems with dvds and diferent audio format, etc.
was i install super ubuntu 9.10 or now it is called super OS .
it is ubuntu with all things you need already installed and the iso it is big around 3gb but you got all u need to have a great experience.

---

### Post by falonyn on 2010-04-02
> **Temposs said:**
> Regarding the DVD playing: have you installed the package called ubuntu-restricted-extras? That should enable dvd playing in addition to a number of other non-free media things.

I have that installed and there is still an issue. Like I said, it will play a Paul van Dyk DVD, of all things, but any others and it opens the player but won't play. Some of the discs it won't even recognise exist. 

I know that my laptop is a little old and the disc drive is kinda on its way out. It is really loud and the plastic vibrates a lot when it reads discs, but it will read any CD and that one DVD, but any other DVD it just doesn't read.

---

### Post by coffeecat on 2010-04-02
> **falonyn said:**
> 1. DVD playback - Alright, so this could simply be my fault for not activating it correctly, but one DVD I have tried works, just none of the rest. How does one DVD work and the rest just not? I have used movie player and VLC. Nothing. 

Apart from ubuntu-restricted-extras, you need the libdvdcss2 library to decrypt encrypted DVDs. Go to:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Add the repository as in the howto, and then install libdvdcss2.

A quicker way is from the terminal...

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```... which will simply download and install libdvdcss2 from Medibuntu without enabling the repository, but I prefer to enable Medibuntu. There's other useful stuff there.

---

### Post by Temposs on 2010-04-02
Yes, where ubuntu-restricted-extras fails, medibuntu is the next thing to try. Follow the instructions here to add it: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then install libdvdcss2 like coffeecat suggests.

---

### Post by Temposs on 2010-04-02
Basically, when a DVD has copy protection(DRM), then you have to use the libdvdcss2 library to decode it. This is a non-free technology, which is why it is not included in Ubuntu, like a number of other packages. Ubuntu is committed to only including free software in the default install and the officially supported packages.

---

### Post by EssexEagle on 2010-04-02
The fact that you are using 10.04 may explain the presence of bugs in general, as it's still in testing...

---

### Post by falonyn on 2010-04-02
I have installed these packages, and I will try a DVD here in a few minutes. 

Does anyone have any solutions for the battery life issue? I just don't understand why I go from almost 3 hours of battery life down to about 1.5 hours. This is the issue I have had for a long time every time I switch to Ubuntu and it is the primary reason I migrate back to Windows. 

I love Ubuntu and would prefer not to have to migrate to another Linux OS if I can help it, but the battery life issue fails a whole lot.

---

### Post by falonyn on 2010-04-02
> **EssexEagle said:**
> The fact that you are using 10.04 may explain the presence of bugs in general, as it's still in testing...

The DVD issue actually appeared before I upgraded to 10.04. So I know that isn't the issue. The issues I am having now with the beta tend to be:


[LIST]
[*]can't go into standby because I can't start up again from standby
[*]going into standby causes all sorts of error messages to pop up when I restart (panic bubble in the system tray)
[*]It presents the ability to run KDE is I want, but it never will launch KDE. It just indexes for search and sits there doing nothing.
[/LIST]

---

### Post by Mark Phelps on 2010-04-02
According to your sig, you're doing Ubuntu development.  That being the case, you should know that beta-related questions are supposed to be posted in the proper beta testing forum, in this case: Development & Programming, Lucid Lynx Testing.

If you go there, you may find the answers to your questions.

Please post there with beta-related issues, not here.

---

### Post by falonyn on 2010-04-02
> **Mark Phelps said:**
> According to your sig, you're doing Ubuntu development.  That being the case, you should know that beta-related questions are supposed to be posted in the proper beta testing forum, in this case: Development & Programming, Lucid Lynx Testing.

If you go there, you may find the answers to your questions.

Please post there with beta-related issues, not here.

The issues and questions that I am talking about are not in relation to using 10.04. They are issues that I had prior to upgrading. The beta issues I understand and are separate. 

The DVD issue and the battery issue are completely unrelated. 

Also, this was not totally a post regarding issues I have, but also stating that I have gone back to Ubuntu and am loving it.

---

### Post by Brandel Valico on 2010-04-02
Don't sweet it Falonyn , I caught that your request for Help was not Beta related. My Advice is the same as you all ready received Medibuntu and  libdvdcss2. Let us know if it works, Either way welcome back to 
Ubuntu. Let me know if you figure out the battery life issue.

---

### Post by theozzlives on 2010-04-02
You were warned several times in the process of downloading Lucid. Ubuntu 10.04 is not meant for production machines! If you want Ubuntu to work, find a final version to use. Otherwise be patient with the bugs as others like me are doing. 10.04 LTS will be released April 29, 2010.

---

### Post by falonyn on 2010-04-02
> **Brandel Valico said:**
> Don't sweet it Falonyn , I caught that your request for Help was not Beta related. My Advice is the same as you all ready received Medibuntu and  libdvdcss2. Let us know if it works, Either way welcome back to 
Ubuntu. Let me know if you figure out the battery life issue.

Thanks. I got the fixes. Just need to test a DVD. I appreciate the help. This community is always quick to help. 

I have a friend that figured the battery issue out, but it is something actually in the kernel which is beyond either of our abilities to fix. It is some way in which the kernel manages processes I think is what he said. Either way, it is something I will be totally reliant on the devs to fix. 

It is good to be back though. Apart from the battery issue, it is a lot nicer. I actually really love the latest versions. It is a really nice user experience. (my friend hates ubuntu because when they updated the kernel and GNOME GUI it became much less stable)

---

### Post by theozzlives on 2010-04-02
> **falonyn said:**
> Thanks. I got the fixes. Just need to test a DVD. I appreciate the help. This community is always quick to help. 

I have a friend that figured the battery issue out, but it is something actually in the kernel which is beyond either of our abilities to fix. It is some way in which the kernel manages processes I think is what he said. Either way, it is something I will be totally reliant on the devs to fix. 

It is good to be back though. Apart from the battery issue, it is a lot nicer. I actually really love the latest versions. It is a really nice user experience. (my friend hates ubuntu because when they updated the kernel and GNOME GUI it became much less stable)

Welcome Back, you were missed.

---

### Post by NightwishFan on 2010-04-02
Battery support merely depends on the tasks you use the laptop for and also the amount of support we get for the acpi of every individual laptops. Think for a second on how Windows would work if it were missing a few critical drivers due to being unsupported by vendors.

Red Hat/Fedora in particular focus on power management so perhaps give Fedora 12 a try. Ubuntu gets about 3 and 1/2 hours on my laptop when the spec on the battery life is 4.

Good luck and enjoy! Happy Ubuntu-ing.

---

### Post by 3rdalbum on 2010-04-02
If there is a problem with battery life, it is hardware-specific. I'm getting more life with my battery on 10.04.

You can try the Powertop program - install it from Synaptic, go to the terminal and type:

```
sudo powertop
```

This program gives you the ability to apply powersaving tweaks that may help.

---

### Post by mörgæs on 2010-04-03
Battery life: A minimal installation works really well on my old machine. Less applications simply means less battery drain.

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961) (there is some bitching in this thread, but still worth reading).

---

### Post by andersq on 2010-04-04
Perfekt! Now that's a nice way to solve things:)

---

