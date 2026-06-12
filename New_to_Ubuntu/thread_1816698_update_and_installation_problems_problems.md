---
title: "update and installation problems problems"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by spleend on 2011-08-02
hi,i am a newbie ,installed ubuntu 11.04
i am able to browse the net through proxy connections..however i am not able to active my update manager..it says chk internet connctn
similarly for ex as i downloaded google chrome it doanloaded fully,however i am not able to install it,the ubuntu software manager says there is smthng wrong
i ran the installer throu terminal but after somtime it said there was some error
i refered to post [http://ubuntuforums.org/showthread.php?t=1226959,it](http://ubuntuforums.org/showthread.php?t=1226959,it) didnt help

solutions??

thank you

---

### Post by Wim Sturkenboom on 2011-08-02
For the GUI, start synaptic; not behind Ubuntu at the moment, but somewhere under option is the option to specify the proxy. This setting will also apply to the update manager.

See [http://ubuntuforums.org/showthread.php?t=1802306](http://ubuntuforums.org/showthread.php?t=1802306) how to bypass the proxy on the commandline; I had the same question and it was answered in there.

---

### Post by spleend on 2011-08-02
running update manager
Error authenticating some packages

"It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages."
"libcurl3
libnss3-1d"

---

### Post by omelette on 2011-08-02
From the toolbar, go System->Preferences and select 'Network Proxy'.  You can change the proxy settings form there.

---

### Post by raja.genupula on 2011-08-02
> **spleend said:**
> i am not able to edit the apt file.showing as read only

edit it with root . use "sudo"  before the command . then you can edit it

---

### Post by Wim Sturkenboom on 2011-08-02
> **spleend said:**
> i am not able to edit the apt file.showing as read onlyYou have to use sudo.

---

### Post by spleend on 2011-08-02
> **omelette said:**
> From the toolbar, go System->Preferences and select 'Network Proxy'.  You can change the proxy settings form there.


i already know to do that

---

