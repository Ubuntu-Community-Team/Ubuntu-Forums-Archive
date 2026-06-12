---
title: "Cant find Ruby 1.9.1 after using &quot;sudo apt-get&quot;"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by caof2005 on 2010-07-12
Hi folks this is the problem I would appreciate your guidance:

I'm trying to install Ruby 1.9.1 in my Ubuntu machine.
As a matter of fact after using the Synaptic Package Manager and selecting the Ruby 1.9.1 (and deselecting the Ruby 1.8.7 ) packages everything runs smoothly, no errors reported.

However when I tried to verify the installation by typing: **ruby -v**

The system prompts the following message:
***The program 'ruby' is currently not installed. You can install it by typing: sudo apt-get install ruby***

I tried to verify the installation (using the synaptic package manager again) and surprisingly all the Ruby 1.9.1 packages are marked as installed.

I also tried to follow the instructions typing **sudo apt-get install ruby**, and it suceeds, however when I re-type *ruby -v*, the version I got is 1.8.7 and that's the one I don't like but the 1.9.1 v

The Ubuntu version that I'm using is 10.04 LTS.

What am I missing or not doing well?

Any help will be very appreciated.
Carlos

---

### Post by Diabolis on 2010-07-12
You have installed BOTH versions, but PATH can only see one. If you type **ruby -v** you'll get 1.8.7. If you want to use the newer version, you must type **ruby1.9.1 -v**.

This is caused by a symbolic link at **/usr/bin**
```

ls -l /usr/bin/ruby

```

If you want to change the default ruby to version 1.9.1, change that symbolic lynk.
```

cd /usr/bin
sudo rm ruby
sudo ln -s ruby1.9.1 ruby

```

DANGER: you'll be modifying a system file through the command line with super user powers. Be sure to know what its going on with this commands.

[[COLOR="Red"]Malicious commands[/COLOR]]("http://ubuntuforums.org/announcement.php?a=54")

---

### Post by caof2005 on 2010-07-12
Thanks a lot... it works great, however I would like to know where really is the Ruby 1.9.1 interpreter.

I mean, it is almost sure that I have to do some kind of maintainance in the future, so before doing my past request I thought to extend the PATH environment variable to include the Ruby1.9.1/bin path, and maybe that would fix my problem.
However I couldnt find where is located the Ruby 1.9.1 interpreter.

Do you have an idea, where or how I can find it?
Thanks in advance.
Carlos

---

