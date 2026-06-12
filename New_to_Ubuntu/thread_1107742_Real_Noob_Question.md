---
title: "Real Noob Question"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by old_dope on 2009-03-27
Before installing Ubuntu 8.10 i would appreciate it if someone could tell me if it would be possible to allow other family members (without admin's Privileges) to use my laptop without them having to login each time and without reducing the laptop's security?

Thanks

---

### Post by Dan_Dranath999 on 2009-03-27
i think 8.10 introduced a "guest account"... but i'm not sure (i'm running 8.04)

---

### Post by [tke]PB506 on 2009-03-27
Ubuntu is an OS just like any other and the main defense of any OS is the end user.  If you are concerned about malware, you are yet again your best defense.  Changes to the OS itself are another story, just make sure the fam doesn't know to put "sudo" in front of commands:P



Edit:  Intrepid does indeed have a "guest" account.  You can be the primary user, when you are finished with your session simply go to the shutdown menu and at the very top it says "Guest Session."

---

### Post by Paqman on 2009-03-27
> **Dan_Dranath999 said:**
> i think 8.10 introduced a "guest account"... but i'm not sure (i'm running 8.04)

To expand on this: the guest account is available once you've logged in, simply go to the fast user switch applet and select "guest". They'll be logged into a temporary account with limited privileges. This temporary account is wiped every time the guest logs out, or if you reboot. Obviously the guest account isn't able to do anything which requires admin rights, such as install software, but you could switch back to your own account in about 5 seconds to do this. When the guest logs out (or you want to switch) you simply put your own password in the get back into your account.

If you want them to have their own personal accounts (so that they have their own browser bookmarks, etc) then they'll have to have a proper account password. There's no way around that without breaking the security model.

---

### Post by old_dope on 2009-03-27
The guest account seems to be exactly what i was looking for.
Thanks for the replies everyone

---

### Post by The Cog on 2009-03-27
You have a bit of a logic problem in your requirements, I think. If they don't log in, how is the OS supposed to know who they are and therefore what priviledges to allow them?

It may be possible to configure the machine to auto-log-in a non-privileged user at boot and then for you to use the switch user feature when you yourself use the laptop. System->Administration->Login Window is where you configure auto-login.

---

### Post by hyper_ch on 2009-03-27
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by mbzn on 2009-03-27
you could go to System>Administration>users and groups; crate an acount for them... then go System>Administration>Login window>Security and set this new account at timed login. I think this is what you're looking for.

Hope it helps

---

