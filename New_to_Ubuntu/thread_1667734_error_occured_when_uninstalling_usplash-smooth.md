---
title: "error occured when uninstalling usplash-smooth"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by sandjora on 2011-01-15
Hello everyone.
I have a problem uninstalling this program. I use Ubuntu 10.04 LTS (GNOME version 2.30.2).

I've tried to uninstall the program with Ubuntu Software center where I got:
"Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

I don't have enabled third party sources. I've tried "sudo apt-get install -f", I got:
"Removing usplash-smooth ...
 Removing any system startup links for /etc/init.d/usplash-smooth-set ...
 Removing any system startup links for /etc/init.d/usplash-smooth-get ...
update-alternatives: error: no alternatives for usplash-artwork.so.
dpkg: error processing usplash-smooth (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 usplash-smooth
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I've tried unistall with Synaptic, I got:
"E: usplash-smooth: subprocess installed post-removal script returned error exit status 2"

I got the program here:
[http://gnome-look.org/content/show.php/Ubuntu+Usplash+Smooth?content=93386](http://gnome-look.org/content/show.php/Ubuntu+Usplash+Smooth?content=93386)

I've even contacted the program owner, but he didn't respond yet.
It seems I have broken dependencies, how ti fix that? Help appreciated.
Regards

---

### Post by drpjkurian on 2011-01-15
If it is broken packages, you can fix it through synaptic package manager by selecting the broken filter..

---

### Post by drpjkurian on 2011-01-15
try synaptic package manager to mend the broken packages..

---

### Post by sandjora on 2011-01-15
Hi.
Thanks for the response.
I've fixed dependency problems via Synaptic, but still cannot remove the program. I get the same error:
"E: usplash-smooth: subprocess installed post-removal script returned error exit status 2"

If I try to update the Update manager I got the same error.

Any other suggestions?
Regards

---

### Post by sandjora on 2011-01-17
Anyone?

I tried:
sudo apt-get purge usplash-smooth
sudo apt-get -f remove
apt-get purge usplash-smooth
dpkg --purge usplash-smooth
dpkg --force- -r usplash-smooth

I always got the same output:
Removing usplash-smooth ...
 Removing any system startup links for /etc/init.d/usplash-smooth-set ...
 Removing any system startup links for /etc/init.d/usplash-smooth-get ...
update-alternatives: error: no alternatives for usplash-artwork.so.
dpkg: error processing usplash-smooth (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 usplash-smooth
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sandjora on 2011-01-22
I found the solution.

1. I removed update-alternatives command from file /var/lib/dpkg/info/usplash-theme-smooth.postrm. Saved the file.
2. Then I forced uninstall usplash-smooth package with dpkg.
3. After that I installed some other theme (default Debian theme I think).
4. Reboot the computer.

---

### Post by drpjkurian on 2011-01-23
Thats a cool solution. Cheers

---

### Post by glamela on 2011-02-04
> **sandjora said:**
> I found the solution.

1. I removed update-alternatives command from file /var/lib/dpkg/info/usplash-theme-smooth.postrm. Saved the file.
2. Then I forced uninstall usplash-smooth package with dpkg.
3. After that I installed some other theme (default Debian theme I think).
4. Reboot the computer.

I've got the same problem, but I dont understand the solution. :oops: Can you explain it for someone with less linux experience? Thanks! :)

---

