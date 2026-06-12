---
title: "No Email"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by G0rd on 2009-05-10
Unable to access emails: I receive this error:

Error while performing operation.

Could not connect to smtp.three.com.au: Connection refused 

Thunderbird gives the same error

I had a similar problem in Windows. It was cured by changing the password, but I can find no way to change it in Evolution.

Can anyone help, as it's impossible to live with Ubuntu with email not working. I'm using Ubuntu 9.04, Jaunty.

---

### Post by AndThenWhat on 2009-05-10
Okay you probably did not setup the e-mail program properly.  There is usually a guide on the website of your e-mail provider that tells you the settings you need for a 3rd party e-mail client.

---

### Post by AndThenWhat on 2009-05-10
Try for your username [email]xxxxx@three.com.au[/email] and SMTP server: smtp.three.com.au if that doesn't work try: smtp.three.net.au

---

### Post by G0rd on 2009-05-10
> **AndThenWhat said:**
> Okay you probably did not setup the e-mail program properly.  There is usually a guide on the website of your e-mail provider that tells you the settings you need for a 3rd party e-mail client.

Thank you for the reply, but I have an identical setup on another computer using 8.10, and it works ok.

---

### Post by alfu on 2009-09-27
In case I needed to do a re-install (I did) , under "File/Backup settings..." I backed up the Evolution parameters into the prompted file "evolution-backup.tar.gz" onto a separate partition.  It must be complete-- it is larger than 22 MB.

After re-installing Ubuntu, starting Evolution launches the Evolution Startup Assistant, which in the second panel prompts "Restore Evolution from the backup file".  I open that filename into the "Please select an Evolution Archive to restore:" field and click Apply, upon which I get an error "Please select a valid backup file to restore."

If I cancel and go on to the empty application, and select "File/Restore settings..." I get the same error.  There seems to be no way around this bug.

---

### Post by clyde9999 on 2009-11-09
I have the exact same problem. Please select a valid backup file to restore.

clyde9

---

