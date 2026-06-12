---
title: "Writing a Script for Network Web Login (New to Scripts)"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by anmlcrckrs on 2007-09-01
I'm using Xubuntu 7.04 with Wifi-Radar and noticed that I can run a script after i connect to a specific network.  I'm totally new when it comes to script writing and haven't been able to find posts that answer.  

Basically I know what I need to do, just not sure how to do it.  

I need to write a script, which I'm not sure how to create/store in Xubuntu
that will  (in order)
1) send an HTTP POST of variables and values to a URL (and hopefully store those values securely,. if possible)
2) it should verify that I have been 'authenticated'
3) i need to poll a URL using HTTP GET until it returns logged_in
4) end the script once logged_in is achieved or an error occurred.  or after a good number of login attempts, say 10.  

So I'm not really sure how to address this, I'm not sure how to create the initial script and where I should store it. and how to make sure that it only runs in the background and doesn't return anything even if it fails.  

This sounds like a lot to me, but then again I've never written a script like this before.  All help is greatly appreciated.

---

### Post by Brandon.Viking on 2007-09-02
For most of that you could use Shell scripts and 'wget' to do what you wanted.

Manual for usage of wget can be found below....
[http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)

it supports post-data or post-file. ... and SSL for security.

and shell scripts are quite easy to pickup .. wget can just be used in the script to do most if not all of what you need.

Check out (google) bash scripting for sites that would turn you into a guru in no time.

Hope that helps.

---

### Post by anmlcrckrs on 2007-09-02
Thanks!  It looks like I should be able to figure out what I need from this.

---

