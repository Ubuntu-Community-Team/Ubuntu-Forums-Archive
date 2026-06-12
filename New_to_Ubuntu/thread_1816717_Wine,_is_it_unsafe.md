---
title: "Wine, is it unsafe?"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by sheshan123 on 2011-08-02
I heard somewhere that installing Wine on Ubuntu makes it vulnerable to windows viruses. Is it true? Did i hear it right? If it is then how do i get safe from such threats. Maybe installing a specific av program or messing in the terminal? :confused:

---

### Post by skatinjj on 2011-08-02
I have been using WINE for years and never even came across an issue with this.

WINE is used to run Windows programs yes but it won't do it without you giving a command to.  Plus, malware designed for Windows is programmed to work on Windows systems and their file trees, not linux file trees.

I suppose it is possible to get a virus installed in the .wine directory if you run a program with malware in it, but it can not go anywhere outside of those windows folders unless its programmed to copy to a linux file path which would be very unlikely for it to be programmed like that IMO.

---

### Post by raja.genupula on 2011-08-02
man i have my word that WINE is safe and good for running windows applications . but if you wanna play games through WINE i am not sure that it can happen .

---

### Post by skatinjj on 2011-08-02
> **raja.genupula said:**
> man i have my word that WINE is safe and good for running windows applications . but if you wanna play games through WINE i am not sure that it can happen .

Unless you are running an application/game that is programmed to install malware you are not going to get it.

Like I said, the virus would have to be programmed to save into the linux file directories and unless its your /home/user folder, it will either not work or ask for your password.  And to my knowledge, no one types in their password unless they know they launched the program =)

WINE = safe IMO

---

### Post by sheshan123 on 2011-08-03
hmm, ty! 
now i feel much safer! :)

---

### Post by CatKiller on 2011-08-03
Someone did an experiment to see if they could deliberately install viruses in Wine. They didn't work. I don't know if that says good things about Linux security or bad things about Wine's compatibility. Even if it had worked, it could only affect Wine's pretend environment, not your Ubuntu environment.

---

