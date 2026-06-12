---
title: "Two pesty questions for dabian to ubuntu convert"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by BorgInPrague on 2010-12-24
I was running debian lenny for a while but someone recommended ubuntu, I installed it and am running without problems. I do have two annoying problems, though:

1. On debian, if my system went down and restarted I was able to login remotely to the Desktop, I can't figure out how to do it in Ubuntu as it keeps asking for keyring password on the local server.  I have searched and tried many solutions, some of them simply did not work and some of them made my system totally inaccessible. I need to be able to access my server while traveling. 

2. On Debian, when I accessed the Desktop remotely over a vncviewer {any] I could go to full screen and I woulld have the desktop nicely over my 27" iMac. }The Ubuntu is running on a Sony Vaio laptop]. Again, I searched and tried many suggestions but none of them worked. This one os not critical, I know, but I don't understand why debian can and Ubuntu cannot.

---

### Post by cariboo on 2010-12-26
> 1. On debian, if my system went down and restarted I was able to login remotely to the Desktop, I can't figure out how to do it in Ubuntu as it keeps asking for keyring password on the local server. I have searched and tried many solutions, some of them simply did not work and some of them made my system totally inaccessible. I need to be able to access my server while traveling. 

You probably have auto-login enabled, that is why you are being asked for a gnome-keyring password. For you the easiest thing to do would be to create a blank keyring password. Go to System->Administration->Passwords an Encryption Keys, right-click password and select change password.

As far as accessing the server remotely, ssh with X-forwarding is one of the more secure ways of doing it. VNC with a weak passwords, is one of the quickest ways to get your system cracked.

---

### Post by BorgInPrague on 2010-12-27
> **cariboo907 said:**
> You probably have auto-login enabled, that is why you are being asked for a gnome-keyring password. For you the easiest thing to do would be to create a blank keyring password. Go to System->Administration->Passwords an Encryption Keys, right-click password and select change password.

As far as accessing the server remotely, ssh with X-forwarding is one of the more secure ways of doing it. VNC with a weak passwords, is one of the quickest ways to get your system cracked.

Thank you very much for your response.

I had tried that but it made my system not accessible at all.  I will try again, now that I have a second recommendation to do it this way.

As to the ssh with X - I do that 90% of the time but was hoping to have a clear access to gnome desktop. Oh well, I guess I can live without that >]

---

### Post by CharlesA on 2010-12-27
If you've got Gnome installed, you can try using [FreeNX]("http://www.nomachine.com/download.php"), but make sure you have a super strong password for your user account if you expose it to the internet. It uses SSH as the transport medium, so it's more secure then VNC, but you still need a strong password, so your box doesn't get cracked.

---

