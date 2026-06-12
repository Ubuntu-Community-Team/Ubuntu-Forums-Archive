---
title: "Speed up acquisition of wireless network"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by dndrich on 2009-02-26
Ubuntupals:

I have a Dell Mini 9 with Intrepid 8.10 installed.  Works really well, I must say.  One little niggling issue is that after I wake the computer from suspend, it takes about 30 seconds to acquire my wireless network.  It works every time, no problem, but it would sure be nice if it were a bit faster.  I am using WEP encryption.  My MacBook acquires almost instantly.  It there a way to speed this up?

---

### Post by hyperyoda on 2009-02-26
> **dndrich said:**
> Ubuntupals:

I have a Dell Mini 9 with Intrepid 8.10 installed.  Works really well, I must say.  One little niggling issue is that after I wake the computer from suspend, it takes about 30 seconds to acquire my wireless network.  It works every time, no problem, but it would sure be nice if it were a bit faster.  I am using WEP encryption.  My MacBook acquires almost instantly.  It there a way to speed this up?

Sounds like Wake-on-LAN.

If you want to suspend and resume and have your wifi working you will need the following script:

# Adapted from AbtZ on [http://ubuntuforums.com/showthread.php?p=5564900](http://ubuntuforums.com/showthread.php?p=5564900)
# Enable wireless after a suspend/hibernate
# For my Acer Aspire One running Ubuntu Intrepid and Madwifi (madwifi-hal-0.10.5.6-r3879-20081204)
# This needs to be executable (chmod +x) and placed in the /etc/pm/sleep.d/ folder
case $1 in
    # We go into hibernate
    hibernate)
    ;;
    # We go into suspend
    suspend)
    ;;
    # We come out of hibernate
    thaw)
        /sbin/ifconfig wifi0 up
    ;;
    # We come out of standby
    resume)
        /sbin/ifconfig wifi0 up
    ;;
    # catch all
    *)
    ;;
esac

Using an editor save this into a file: /etc/pm/sleep.d/10-wifi
Now run:
$ sudo chmod +x /etc/pm/sleep.d/10-wifi

Zach

---

### Post by dndrich on 2009-02-26
Well, my wifi definitely works after a suspend and wake, it just takes about 30 seconds to acquire.  Does your script just make that faster?  My connection definitely occurs every time, but it just takes more time than I would like.

---

### Post by dndrich on 2009-03-01
Hyperyoda:

I tried your interesting script.  Thanks for that work.  Unfortunately, it didn't speed things up at all.  I have never had a problem with it acquiring, it is just that it takes about 30 seconds.  Perhaps that is an inherent problem with the network manager that cannot be sped up with this configuration.  Oh, well!

---

### Post by Sarai the Geek on 2009-03-01
Mine does this as well, but it doesn't even matter whether the network is encrypted or not. It's not a problem so much as it is an annoyance.

---

### Post by dndrich on 2009-03-01
Yeah, just an annoyance.  Nothing logs on faster than my MacBook.  It is a delay of only seconds.  I wonder how they do it?

---

### Post by kerry_s on 2009-03-01
the difference is linux shuts off the wifi when suspended, a mac keeps the connection even when suspended.

that might not be worded right, but i hope you get the meaning.

---

### Post by Sarai the Geek on 2009-03-01
> **kerry_s said:**
> the difference is linux shuts off the wifi when suspended, a mac keeps the connection even when suspended.

that might not be worded right, but i hope you get the meaning.

Is there a way to change that?

---

### Post by Yashiro on 2009-03-01
Try assigning yourself a static IP.
If you can do it from your router that would be an ideal first test.

---

### Post by kpmoore on 2009-03-01
I'm also having this problem. It's worth noting that when the system comes out of suspend mode, the whirling connection status  in the notification area (with the two green lights) is frozen i.e. not whirling. It looks like its stuck for a while and then all of a sudden its connected.

---

