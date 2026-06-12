---
title: "Kompozer keeps on closing down"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-12-26
Hello Everybody,

I'm trying to design a website with Kompozer, but whenever I try to add an image it closes. If I use a template and try to change text colour, it closes. Is it something I'm doing / not doing? 

I've been using Frontpage for years and now that I've abandoned Windoze for Ubuntu I would like to be able to design and maintain relatively simple sites in Ubuntu. Kompozer seems ideal but I can't work with a program that shuts down whenever you try to alter something. Bluefish and Screem are too technical for me. Is there another open source alternative to Kompozer?

Thanks,

Charlie

---

### Post by chrisod on 2008-12-26
What version of Ubuntu are you using? What are your system specs?

I've never had any problems with Kompozer. Make sure you have the most current version with:

```
sudo apt-get install kompozer
```

If it reports that you are up to date you might try uninstalling and reinstalling it.

---

### Post by Charlie Chick on 2008-12-27
I'm using Ubuntu 8.10 on a Dell with a Pentium 4, 2Gb of Ram and a 750Gb hdd. I checked that the version of Kompozer I have is the same as that on the Kompozer website. I've already tried uninstalling and reinstalling it, to no avail. Are there any alternatives at the same level?

---

### Post by chrisod on 2008-12-27
Start Kompozer from the command line. When it crashes you should see a bunch of error output in the terminal window. Post that here, it might give us an idea where to look for the cause.

---

### Post by noe2008 on 2008-12-28
> **chrisod said:**
> Start Kompozer from the command line. When it crashes you should see a bunch of error output in the terminal window. Post that here, it might give us an idea where to look for the cause.

I am using ubuntu 8.10 and I have exactly the same problem. I tried re-installing several times. The error message I get from the terminal is: "Segmentation fault".

Thanks!

noe

---

### Post by chrisod on 2008-12-28
A seg fault typically means the program crashed trying to access memory it doesn't have access to. It may be that Kompozer isn't compatible with 8.10 yet. I don't have any problems with it in 8.04.

---

### Post by Charlie Chick on 2008-12-28
I've been doing some experiments. If I open an already existing website in Kompozer, it'll crash; if I start a new one it works OK. Maybe it simply doesn't like other program's websites?

---

### Post by chrisod on 2008-12-28
That's kind of odd as HTML really shouldn't be crashing an editor. Are you trying to open sites that are online somewhere? Not having write access to a remote server should not kill the program, you should just get an error message.

If you save a problem site to  your hard drive with Firefox and then open it in Kompozer do you get the crash? If not, that might at least point to it being a network or maybe a permissions issue. If you can repeat the crash you might want to submit a bug report. Not sure how active Kompozer development is though.

---

### Post by Charlie Chick on 2008-12-29
The site I'm trying to open was created in MS Frontpage about 8 years ago and, as I no longer use any MS products, I'm trying to do everything in Linux. The files reside on my hard drive and I have full write access to the server. Maybe Kompozer just isn't compatible with 8.10.

Do you know of any other easy web editor for Ubuntu?

---

### Post by impact on 2008-12-29
Multiple solutions are mentioned in this thread (windows version of composer with wine or manually installed version of kompozer):

[http://ubuntuforums.org/showthread.php?t=988682&highlight=kompozer](http://ubuntuforums.org/showthread.php?t=988682&highlight=kompozer)

---

### Post by jorge ortega on 2008-12-29
Exactly the same happened to me when I upgraded to 8.10. By looking at other threads it seems a problem of incompatibilities with Ibex (for the time being). I personally had to go back to Hardy Heron which solved the problem. I am not sure but a solution might be to work with Hardy Heron (and Kompozer) from a live cd which you should not have problem getting.

---

### Post by JC Cheloven on 2008-12-29
Here you are:

[http://ubuntuforums.org/showthread.php?t=988682&highlight=kompozer&page=2](http://ubuntuforums.org/showthread.php?t=988682&highlight=kompozer&page=2)

---

