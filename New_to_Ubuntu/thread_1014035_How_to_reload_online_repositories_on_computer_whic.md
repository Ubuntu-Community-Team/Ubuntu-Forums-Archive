---
title: "How to reload online repositories on computer which doesnot have internet connection."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-12-17
Synaptec Package manager has a method by which we can generate list of necessary pacakges from system with no internet connection, take a list to computer with internet connection, download the packages, copy back on the original system without internet and install then through package manager.

I want to know how to reload the online repositories at first place on system without internet connection?

---

### Post by rlunger on 2008-12-17
> **Guruprasad said:**
> Synaptec Package manager has a method by which we can generate list of necessary pacakges from system with no internet connection, take a list to computer with internet connection, download the packages, copy back on the original system without internet and install then through package manager.

I want to know how to reload the online repositories at first place on system without internet connection?

You can't.  You'd have to first download (from another computer) the list of update repositories, then go back and give those to Synaptic.  After that, it will tell you what packages you need to specific apps, and then you'll have to download those.  It might be easier to just look at the repositories on the website.  It will tell you which packages/dependencies you'll need for a certain app, and then get those to.

---

### Post by Guruprasad on 2008-12-17
> **rlunger said:**
> You can't.  **[COLOR="Red"]You'd have to first download (from another computer) the list of update repositories, then go back and give those to Synaptic.[/COLOR]**  After that, it will tell you what packages you need to specific apps, and then you'll have to download those.  It might be easier to just look at the repositories on the website.  It will tell you which packages/dependencies you'll need for a certain app, and then get those to.

Hi

Do you mean After reloading the repositories on the computer with internet can we give those to synaptic on computer without internet? If yes how?

---

### Post by rlunger on 2008-12-17
> **Guruprasad said:**
> Hi

Do you mean After reloading the repositories on the computer with internet can we give those to synaptic on computer without internet? If yes how?

I'm not running my Ubuntu partition this minute but you can add repositories, either from the Internet or disk to the list of sources your system checks. Most likely, you can do this through Synaptic or Add/Remove.  I've done it using YaST under Suse and I'm pretty sure the process will work similarly.  As I mentioned, the repository website will tell you what packages you need for the apps you want, so you could just download them from there, without having to update the list of available packages on your un-connected machine.

---

