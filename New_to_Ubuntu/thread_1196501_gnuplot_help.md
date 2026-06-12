---
title: "gnuplot help"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by f00k3r on 2009-06-25
Hi,

  I just installed gnuplot 4.2 and have just started working on it. However, I'm not able to 'set terminal x11' since it displays 'unknown or ambiguous terminal type'. When I type plot sin(x), it doesn't display anything on the screen. How do I correct this? Thanks for your help.



Thanks,
Bharat.

---

### Post by mltucker on 2009-06-25
How did you install it?

```

set term x11

```

and

```

set terminal x11

```

both work fine for me :-/

---

### Post by ad_267 on 2009-06-25
Works here too. What version of Ubuntu do you have and did you install from the Ubuntu repositories? If not I suggest you uninstall it then reinstall using the version in the repositories. If you did install from the repository then make sure you have the gnuplot-x11 package installed and not just gnuplot-nox. See [here]("http://www.psychocats.net/ubuntu/installingsoftware") for more information on installing software in Ubuntu.

---

### Post by f00k3r on 2009-06-25
Hi,
 
   I installed the gnuplot package from sourceforge. Do I need to install something extra for it to work?
This is the link which I used:
[]("http://sourceforge.net/project/showfiles.php?group_id=2055") 

Thanks,
Bharat.

---

### Post by f00k3r on 2009-06-25
[http://sourceforge.net/project/showfiles.php?group_id=2055]("http://sourceforge.net/project/showfiles.php?group_id=2055")

---

### Post by ad_267 on 2009-06-25
I would recommend you remove it and just install the version from the Ubuntu repositories, unless there's any features you really need in the version compiled from source. It's a lot simpler to install applications from the repositories rather than compile them yourself.

If you do want to compile from source you have you will have to read the documentation and determine what libraries you need to compile with support for the x11 terminal and make sure you pass the correct options to the configure script.

Running "./configure --help" I can see it looks like you need to use the --with-x option. Alternatively it looks like there's a wxwidgets terminal you could use which would provide more features instead of the default x11 terminal.

---

### Post by f00k3r on 2009-06-25
Yeah, that sounds good. I'll try that.


Thanks,
Bharat.

---

