---
title: "cron help"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Thomtzvi on 2009-01-16
Hello,

I am looking to automate commands to update ubuntu on my server using cron. If I insert the following into crontab will it work?

```
20 3 * * 1,3,5,7 sudo full-upgrade
```

Do I have to set up the cron job as root to avoid needing to enter the sudo password every time?

Thank you.

---

### Post by hyper_ch on 2009-01-16
you will need to add this to the root cron....

(1) become temporary root
```

sudo -i

```

(2) then I'd put that into a cron.txt file (I just think it's easier to edit a txt file whenever you feel like it)
```

20 3 * * 1,3,5,7 full-upgrade

```

(3) add it to cron
```

crontab cron.txt

```

(4) while still as temporary root, check if it was added:
```

crontab -l

```

(5) exit root
```

exit

```

OR you could just add it like this:

```

sudo crontab -u root cron.txt

```

---

### Post by iaculallad on 2009-01-16
No need to include the sudo command on your cron jobs as editing crontab requires administrative privilege. Sample below on automatic update and upgrade.

Create a script named autoupdate.sh, file content:

> #!/bin/bash
apt-get -y update
apt-get -y upgrade
updatedb

On your terminal:

```
sudo crontab -e
```

and create the job as:

> 11 11 * * * /path/to/autoupdate.sh

HTH.

---

### Post by dm993 on 2009-01-16
I'm also having crontab issues. I have a script that works perfectly fine if I manually execute it, but I scheduled it with crontab and it had never ran.

I did the following:-
$ sudo crontab -e
* * * * * /path/to/script.sh

$ sudo crontab -l verifies it's there.

I don't have a cron.allow or cron.deny in /etc but don't think this is my problem.

I'm pretty confused about this, can you guys think what I might have missed??

---

### Post by hyper_ch on 2009-01-16
I think it misses some paths in there... cron does not have all paths included like the normal user.

---

