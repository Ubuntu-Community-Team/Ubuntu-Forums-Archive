---
title: "Decrypting Launchpad's email message"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by chris1950 on 2009-08-18
I am trying to decrypt the validation message from Launchpad. I followed each instruction as outlined in [GnuPrivacyGuardHowto]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto?action=fullsearch&context=180&value=linkto%3A%22GnuPrivacyGuardHowto%22") . No matter what I do I still can not decrypt the message. Even after changing permissions (777).

See commands below

chris@Compaq-Laptop:~$ gpg -d launchpadmessage.txt
gpg: WARNING: unsafe permissions on configuration file `/home/chris/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/chris/.gnupg/gpg.conf'
gpg: can't open `launchpadmessage.txt'
gpg: decrypt_message failed: file open error

---

### Post by aesis05401 on 2009-08-18
Forgive me, I don't understand.  What email is this from Launchpad?  I have an account over there and have not needed to decrypt any emails to read them.

If you run the 'file' command on the file what file type is returned?

---

### Post by chris1950 on 2009-08-18
I opened Krusader, highlighted the file, typed file command and got the error -- could not decrypr did not have decryption key. I don't understand this.

---

### Post by tripleee on 2009-09-10
The error message looks like you're in the wrong directory, or there is something fundamentally wrong with the file, or you have a GPG problem.  Can you view the encrypted file with less?  Can you decrypt other encrypted files?  (The GPG warnings look like just warnings but it could be refusing to run because of those.  Does it help if you fix the things it warns you about?  You should not have a world-readable home directory, etc.)

Chmod 777 is the wrong answer to every question you can reasonably imagine.  chmod 644 or in this case even 400 is probably more like what you want.  (4 means read, 6 means read and write, 7 means read+write+execute, for owner, group, and world, respectively, in that order.)  I don't think that's the problem here, but I can't help but remark on this.

---

