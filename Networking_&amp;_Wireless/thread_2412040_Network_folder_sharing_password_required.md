---
title: "Network folder sharing: password required"
date: 2019-02-07
forum: Networking &amp; Wireless
---

### Post by dysprosium-1218-x on 2019-02-07
At my workplace, I have folders that are shared within the work's network.
On Windows 10, I can access those shared folders without issue, I just have to write the adress after \\ in the Network tab.
On Ubuntu, I use the smp://<adress> function, but it prompts me for a password which I have no idea what it is, nor if it even exists. It's asks for a ghost password.
There is a "sign in anonymously" option without a password, but that doesn't work, it keeps prompting me.

---

### Post by TheFu on 2019-02-07
Please, correct incorrect details above.

I can only guess that an incompatible SMB version is being used either by the client or the server.  Check that.  The samba log files should say something.

If the server doesn't allow "guest" access, then you won't be able to connect without a login.

---

### Post by dysprosium-1218-x on 2019-02-11
What do you mean with correcting the incorrect details?
And how do I show you the samba log files?

---

### Post by TheFu on 2019-02-11
> **dysprosium-1218-x said:**
> What do you mean with correcting the incorrect details?
And how do I show you the samba log files?

smp?  Details matter.  Using "smp" will never work.

I'm not interested in looking through the samba log files. YOU should do that. Read what they say, look for errors and warnings, then almost always a google search for either of those types of issues will yield corrective action. Almost all log files on any Uinx system will be in /var/log/ or somewhere down that path.  When anyone says to check the log files, that is where to begin.  Googling "ubuntu logs" or "ubuntu samba logs" would have gotten you there too.

Sometimes there is a bug, but most recently, the issues seem to be almost always related to Windows10 changing the default SMB version supported, so the same version needs to be allowed on the Unix side.

I'm not a samba expert, just someone who has gotten samba to work over the last 20+ yrs with few issues.  Since the early 2000s, my setup has been trivial, so it is likely I cannot provide specific answers. Sorry.

---

### Post by dysprosium-1218-x on 2019-02-11
> **TheFu said:**
> smp?  Details matter.  Using "smp" will never work.

I'm not interested in looking through the samba log files. YOU should do that. Read what they say, look for errors and warnings, then almost always a google search for either of those types of issues will yield corrective action. Almost all log files on any Uinx system will be in /var/log/ or somewhere down that path.  When anyone says to check the log files, that is where to begin.  Googling "ubuntu logs" or "ubuntu samba logs" would have gotten you there too.

Sometimes there is a bug, but most recently, the issues seem to be almost always related to Windows10 changing the default SMB version supported, so the same version needs to be allowed on the Unix side.

I'm not a samba expert, just someone who has gotten samba to work over the last 20+ yrs with few issues.  Since the early 2000s, my setup has been trivial, so it is likely I cannot provide specific answers. Sorry.

I do not wish any further 'advice' from you.

---

### Post by howefield on 2019-02-11
> **dysprosium-1218-x said:**
> I do not wish any further 'advice' from you.

There you go.. thread closed.

Job done.

Happy to help :)

---

