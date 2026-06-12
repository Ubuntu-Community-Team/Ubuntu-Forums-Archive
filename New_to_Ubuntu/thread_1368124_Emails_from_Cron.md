---
title: "Emails from Cron"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by Jloser on 2009-12-30
Currently I have a cron job that completes all system updates.  Whenever this runs I get an email with the results.  As part of my preparations for 2010 I am trying to reduce the volume of email that I receive.  I only want to get an email if updates were applied.  Any ideas on how to accomplish this?

Here is my update script:
```
#!/bin/bash
sudo apt-get update > /dev/null
echo -e '\n****\nStarting package updates\n****\n'
sudo apt-get -y upgrade
echo -e '\n****\nStarting distribution updates\n****\n'
sudo apt-get -y dist-upgrade
echo -e '\n****\nStarting cleanup\n****\n'
sudo apt-get -y clean
sudo apt-get -y autoclean
sudo apt-get -y autoremove

```

Here is the email when it needs to be ignored:
```
****
Starting package updates
****

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

****
Starting distribution updates
****

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

****
Starting cleanup
****

Reading package lists...
Building dependency tree...
Reading state information...
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So basically if the email looks as in the example I want it to be ignored by the system and not sent.

---

### Post by Bachstelze on 2009-12-30
Simplest way would be to dump everything to a file instead of standard output, and decide whether to send email or not based on the contents of the file when everything is done.

---

### Post by Jloser on 2009-12-30
I like that idea, but not entirely sure how to implement it.  Would it be best to create an entirely new script or to modify the cron job?

---

### Post by Jloser on 2009-12-31
So after some tooling around I figured this out:
```
#!/bin/bash
#Update all software and send email if any updates were applied
#12/31/09

#Update system
apt-get update > /dev/null
echo -e '\n****\nStarting package updates\n****\n' > t.out
apt-get -y upgrade >> t.out
echo -e '\n****\nStarting distribution updates\n****\n' >> t.out
apt-get -y dist-upgrade >> t.out
echo -e '\n****\nStarting cleanup\n****\n' >> t.out
apt-get -y clean >> t.out
apt-get -y autoclean >> t.out
apt-get -y autoremove >> t.out


#Compare to known 'null' file, if different add email and subject then send mail
if diff t.out noupdates.txt >/dev/null ; then
  :
else
  sed -i '1i TO: my.email@here.com' t.out
  sed -i '2i SUBJECT: Updates Applied' t.out
  ssmtp -t < t.out
fi

```

Is this an efficient way to complete this task?  Any other suggestions?

---

