---
title: "/etc/hosts"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by olddai on 2010-11-29
I would like to edit the /etc/hosts file to prevent sites, is this possible? If so does anyone know of a tutorial which covers this and are there lists of known malware or bad sites i can add to the /etc/hosts file

---

### Post by theozzlives on 2010-11-29
> **olddai said:**
> I would like to edit the /etc/hosts file to prevent sites, is this possible? If so does anyone know of a tutorial which covers this and are there lists of known malware or bad sites i can add to the /etc/hosts file

I believe that would be the /etc/hosts.deny file. However 99.99% of malware out there is for Windows, so I don't worry about it.

---

### Post by sisco311 on 2010-11-29
I'm using [this]("http://hostsfile.mine.nu.nyud.net/downloads/updatehosts.sh.txt") script to regularly update my hosts file. 

[http://hostsfile.mine.nu.nyud.net/](http://hostsfile.mine.nu.nyud.net/)

---

### Post by philinux on 2010-11-29
> **olddai said:**
> I would like to edit the /etc/hosts file to prevent sites, is this possible? If so does anyone know of a tutorial which covers this and are there lists of known malware or bad sites i can add to the /etc/hosts file

According to this it's easy. [http://www.addictivetips.com/ubuntu-linux-tips/how-to-block-unwanted-website-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-block-unwanted-website-in-ubuntu-linux/)

Make sure you use this command though.```


gksudo gedit /etc/hosts
```

---

### Post by StuMcBill on 2010-11-29
> **sisco311 said:**
> I'm using [this]("http://hostsfile.mine.nu.nyud.net/downloads/updatehosts.sh.txt") script to regularly update my hosts file. 

[http://hostsfile.mine.nu.nyud.net/](http://hostsfile.mine.nu.nyud.net/)

Forgive me as I am a bit of a n00b, but how would I run this script?

Do I have to chmod it to mark it excecutable?

---

### Post by mikewhatever on 2010-11-29
Yes, chmod +x updatehosts.sh, then run it with sudo ./updatehosts.sh.

---

### Post by sisco311 on 2010-11-29
> **StuMcBill said:**
> Forgive me as I am a bit of a n00b, but how would I run this script?

Do I have to chmod it to mark it excecutable?

Yes, you have to make it executable and run it as root.

Download the file:
```
w3m http://hostsfile.mine.nu.nyud.net/downloads/updatehosts.sh.txt | sudo tee /usr/local/bin/update-hosts
```

Mark it as executable:
```
sudo chmod 0755 /usr/local/bin/update-hosts
```

Install its dependencies:
```
sudo apt-get install wget unzip tofrodos grep
```

To update the hosts file, run:
```
sudo /usr/local/bin/update-hosts
```

You can create a cron job to run it automatically. Edit the crontab file:
```
sudo crontab -e
```
and append it with:
```
@daily    ID=update-hosts    /usr/local/bin/update-hosts
```
Save it and exit (Ctrl+x, y, Enter).

---

### Post by StuMcBill on 2010-11-29
Thanks sisco311.

That worked fine, didn't do the automated update command though, would rather do it manually while I am still getting to grips with Ubuntu.

Stu

---

