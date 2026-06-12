---
title: "Enabling flash player with chromium"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by cK` on 2010-04-14
Hello i am trying to enable my flash plugin for chromium not just firefox.

I have copyed libflashplayer.so and put it in /usr/lib/chromium-browser/plugins


I have also right clicked the icon i use to open my browser and put the follow in the command line.

hromium-browser --enable-plugins

Firefox can view flash videos great, however chrome does not work.


Any suggestions?

---

### Post by -humanaut- on 2010-04-14
'sudo apt-get install ubuntu-restricted-extras' should do the trick flash has been working in Chromium just fine for me. Are you using 64bit?

---

### Post by cK` on 2010-04-14
Wonderful! it works.

Would you mind explaining to me what that command just did?

My computer is 64bit capable but i am running 32 i believe.

---

### Post by cK` on 2010-04-14
More specifically what is unbuntu restricted extras?

---

### Post by -humanaut- on 2010-04-14
That command just installs patent encumbered software such as Flash Mp3 support and MSCore fonts 'Apt' is the package manager in ubuntu and Debian there's ALOT that it is check out the linux documentation project if you want to learn more about aptitude/Apt 
[http://tldp.org](http://tldp.org)

---

### Post by cK` on 2010-04-14
With that installed was changing the properties command line and copy/pasting the plugin into my chromium plugin file unnecessary? 


Thanks for your help, and the link i will check it out.

---

