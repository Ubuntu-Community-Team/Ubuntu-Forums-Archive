---
title: "Netatalk Build Conflict Hardy amd64 Server"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by kazooless on 2008-06-25
I have been trying every possible thing I can find on the net and this forum regarding encrypted authentication and Leopard, but to no avail. I am successful setting up guest access, so I know that it is partially working.

Specifically, I am sure the problem is that it is not building the /usr/lib/netatalk/uams_dhx.so module because the package heimdal-dev conflicts with libkrb5-dev, and the libkrb5-dev shows up as a dependency. There is a comment on a blog about using pbuilder to "fix" the circular dependency conflict, but I am at a loss as to how to do this. Here is a link to that comment: [http://www.blackmac.de/archives/58-Make-Netatalk-talk-to-Leopard-Mac-OS-X-10.5.html#c108](http://www.blackmac.de/archives/58-Make-Netatalk-talk-to-Leopard-Mac-OS-X-10.5.html#c108)

And a quote of the relevant part:

> Thanks for the link to that posting, Cody -- it turns out I too was missing libssl-dev. I had to solve the circular dependency problem by running /usr/lib/pbuilder/pbuilder-satisfydepends, and with those two in place, once I re-ran ./configure, it finally reported that it was configured to build the DHX support. I'm finally reconnected to my Linux box. Huzzah!


I try running the pbuilder-satisfydepends command and it gets rid of heimdal-dev. So what gives?

And please don't suggest to just connect with cleartext. LOL

Thanks for any help. I'm sure I'm not the only one that will encounter this problem.

kazooless

---

### Post by kazooless on 2008-06-25
Doesn't it happen so often that only AFTER you post a question, you try once again and somehow it works? Maybe it is the difference between working on it after midnight and in the morning after a night's sleep.

Anyway, re-reading and re-trying this:

[http://blog.wearesakuzaku.com/making-netatalk-work-on-debian-with-leopard/](http://blog.wearesakuzaku.com/making-netatalk-work-on-debian-with-leopard/)

> As it turns out, I wasn’t looking at the build output carefully enough. This post mentions to look for the line ‘Configure summary’, and for me it didn’t list the DHX UAM as being built. Looking at the output from the configure script, I realized I didn’t have libssl-dev installed. After installing that, everything went smoothly.

just now worked for me.

I think that "sudo apt-get build-dep netatalk" removed "libssl-dev" installed from the previous command "sudo aptitude install devscripts cracklib2-dev dpkg-dev libssl-dev." Not 100% sure.

But in this case, after following this:

> $ mkdir -p ~/src/netatalk 
$ cd ~/src/netatalk 
$ sudo aptitude install devscripts cracklib2-dev dpkg-dev libssl-dev 
$ apt-get source netatalk 
$ sudo apt-get build-dep netatalk 
$ cd netatalk-2.0.3 


I ran this:

> sudo aptitude install libssl-dev 

and then I ran the rest of the commands:

> 
# sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -us -uc 
# sudo debi 
$ sudo echo "netatalk hold" | sudo dpkg --set-selections 


Now, after making sure the /etc/netatalk/afpd.conf file is configured correctly, it works.

Hope this helps others. Many thanks of course to [http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication](http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication)

and [http://blog.wearesakuzaku.com/making-netatalk-work-on-debian-with-leopard/](http://blog.wearesakuzaku.com/making-netatalk-work-on-debian-with-leopard/)

kazooless

---

