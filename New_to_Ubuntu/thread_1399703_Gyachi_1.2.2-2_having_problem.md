---
title: "Gyachi 1.2.2-2 having problem"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by black scorpio on 2010-02-06
Hi got a problem on connecting YM using Gyachi 1.2.2-2 just yesterday after an update occur. Or i don't know if there is any problem regarding Gyachi? Anybody experience same problem i have. It say incorrect password or user name in fact it was correct. And some strange situation I in counter if I log-in using other account from YM it will connect the two acct. But the other two acct didn't. Please help...

---

### Post by Paulieb on 2010-02-06
I'm having the same problem, too. Ubuntu updated the kernel today, and since that update, I've been unable to connect to the Yahoo server. I put in my correct user name and password to connect, but receive a message in return that either my user name or password is incorrect. I wonder what's up, and what i can do to work around this problem. Anyone have any help to offer? I'd be grateful. Thanks.

---

### Post by Nicole on 2010-02-06
Bumping this, because I've had the same problem after updating the kernel. Any help would be much appreciated!

---

### Post by sports fan Matt on 2010-02-06
Same result here with 9.04.  Thought it was just me.

---

### Post by loell on 2010-02-06
probably attach your packet logs, it might be useful.

try enabling "packet debugging" and "log debug to file" in the connections menu , restart gyachi and try logging in (after the error comes up )

go to /.yahoorc/gyach/log/gyachi-debug/ , there should be a text file there, copy paste the content to [http://pastebin.com/](http://pastebin.com/)

then post the link here, so the developer can look at it, when he's already available.

---

### Post by Paulieb on 2010-02-06
Thank you for your help. I've followed your directions, and the text log results have been posted at [http://pastebin.com/m3e681579](http://pastebin.com/m3e681579).

I hope this helps to possibly find out what has gone wrong with the kernel update.

Thanks again.

---

### Post by needhelppeeps on 2010-02-07
Im having the same problem except some accounts work and some do not. A couple other people use this machine (all the same ubuntu user account) and one of us can log in! However one my yahoo and another yahoo it keeps saying bad password even though we know it's right and we can both sign in via empathy

---

### Post by loell on 2010-02-07
a fix has just been rolled out, v 1.2.4

if you are in karmic use this  PPA repo

[https://launchpad.net/~baudm/+archive/ppa/+packages]("https://launchpad.net/~baudm/+archive/ppa/+packages")

---

### Post by Paulieb on 2010-02-07
Thanks once again, loell. I unfortunately cannot install the 1.2.4-0.1 update. When I try to install using the deb package manager, I get the following error message: "Error: Dependency is not satisfiable: gyachi-data (= 1.2.4-0.1~baudm1)"

(I wonder what that all means?)

In any event, despite your helpful efforts so far, it appears that I remain unable to use Gyachi. Any suggestions as to what I might try next?

Thanks again.

---

### Post by loell on 2010-02-07
in the repository there is also **gyachi-data.deb** which you need to install, i guess you only downloaded gyachi_1.2.4-0.1.deb?

there's always pidgin,empathy and kopete.

---

### Post by Paulieb on 2010-02-07
I guess I'm just too much of a noob, loell. I didn't recognize the gyachi-data deb file earlier when i visited the repository.

I've now downloaded and installed the gyachi-data deb file, and all is back to being good. I'm back to being able to run gyachi and log into to my Yahoo chat account. This is great as I much prefer to use gyachi to using either pidgin or empathy.

I thank you again for your help (and your patience with folks like me who are relatively new to Ubunbtu and not yet technically savvy enough to figure out stuff on our own.) You've been great!

---

### Post by De Rookie on 2010-02-07
> **loell said:**
> a fix has just been rolled out, v 1.2.4

if you are in karmic use this  PPA repo

[https://launchpad.net/~baudm/+archive/ppa/+packages]("https://launchpad.net/~baudm/+archive/ppa/+packages")

Loell nice response time.. I'm still using Jaunty the package for Karmic doesn't install.

---

### Post by needhelppeeps on 2010-02-10
I was thinking about installing this, but is this definitely a legitimate site. I really do not like installing things from various websites. That's how windows users used to end up with trojans (before someone decided infected websites were a better method and seems to be the primary way now). Why don't they just work the fix into primary repo?

---

### Post by sean.nautica09 on 2011-02-24
I am facing the same prob. But I have maverick build x86_64.
I cant install those packages as those are x86. Help...

---

### Post by xx58 on 2011-03-02
I have DEBIAN 6.0 Is there place where I can get Gyachy package? Thanks:rolleyes:

---

