---
title: "Administration - Keyring Manager"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by meddyliol on 2009-01-18
I have been trying to open the Keyring Manager which is supposed to be in Administration. I cannot see it with Ubuntu 8.04.
Another question is: Can I upgrade to 8.10 without doing a complete re-install? Or do I have to completely re-install losing all of the applications etc downloaded with the applications manager. I might not want to do it but just in case. 8.04 seems to run fairly well except for having to log in every time with the Keyring password. I have been trying to follow the many guides but still having problems.

Thanks

Brian :(

---

### Post by stoogiebuncho on 2009-01-24
Well, I think the Keyring Manager is System > Preferences > Encryption and Keyrings.

If it's asking you for a password every time you start up, the problem could be with network manager, which is known for doing that.  You might try Wicd instead: [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

You can upgrade to 8.10 if you want to.  First, back up your files.  You shouldn't need to, but there's always the chance of something going wrong, so better safe than sorry.

Then go to System > Administration > Software Sources.  Go to the Updates tab.  At the bottom there's a place that says Show New Distribution Releases.  It's default is to show LTS (Long Term Support) releases only.  You can change that to Normal Releases.

Then go to System > Administration > Update Manager.  It should now have a button near the top to upgrade to 8.10.

---

### Post by diablo75 on 2009-01-24
Here ya go!

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

