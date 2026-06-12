---
title: "CRON job apparently not executing"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by ChrisRChamberlain on 2010-07-23
Hi all

Have a fresh install of Ubuntu server 10.04 and have created a file - /var/www/zoneedit.sh

The content of the file is ```
MAILTO=chris@xxx.co.uk
wget -O - --http-user=MyName --http-passwd=Password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.xxx.co.uk'
```

The crontab entry is ```
*/15 * * * * /var/www/zoneedit.sh
```

and crontab -l shows the entry

In the properties of the file /var/www/zoneedit.sh, 'Open With' is set as crontab, Permissions, Access - Read and write.

However the changes are not made at [www.zonedit.com](www.zonedit.com)

Any ideas as to what is not working?

TIA

Chris

---

### Post by DaithiF on 2010-07-23
Hi,
Firstly, does the wget command do the right thing when you run it from the terminal?  I mean just the wget command itself, not the zoneedit.sh script you have wrapped it with.

Assuming yes, then some things about the script itself:
1. the script needs to be somewhere which is accessible to your user id for you to be able to run it.   /var/www is (probably) not writeable by your user id, so I would suggest you start out putting the script in your home directory, at least until you have it working.
2. The script needs to be executable.  You mention read and write permissions, but not whether it is executable.  
```
chmod +x zoneedit.sh
```to make it executable.
3. I don't know why you have the MAILTO line, and the 'open with crontab' thing is wrong, crontab doesn't need file associations like that to run.   However neither of these should prevent the script from running, so once you've done 1. and 2., then try running it manually:
```
./zoneedit.sh

```4. if that works, then next step is to see if it can now run ok under cron

good luck

---

