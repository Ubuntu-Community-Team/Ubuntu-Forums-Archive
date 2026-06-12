---
title: "NAS backup device for a Linux machine?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2009-12-02
I want a simple NAS to backup the machines in the house. Most have software to automate the process for our PCs and Macs, but I haven't seen one with a Linux option. Does something like this exist? What about one with easy to find/install aftermarket software?

Thanks, 

Rhythm

(Not sure if this is the right forum, or if Hardware would have been better. But since I'm an absolute beginner, I thought this would be best. Please move as necessary, and accept my apologies.)

---

### Post by Locke_99GS on 2009-12-02
You can write your own backup script (rsync is awesome!) or use any existing backup scripts/softwares, and just direct it to the network device. Search Software Centre or Synaptic for "backup" and "back-up", ought to yield plenty of options.

---

### Post by Rhythmdvl on 2009-12-02
> **Locke_99GS said:**
> You can write your own backup script (rsync is awesome!) or use any existing backup scripts/softwares, and just direct it to the network device. Search Software Centre or Synaptic for "backup" and "back-up", ought to yield plenty of options.
I could if I weren't an idiot :) 

Here's my problem. I currently have a Linksys NAS200 (it's getting replaced because it's painfully slow), and I've never been able to figure out how to get automated backups to work. For example, I have sbackup installed (and have un/and reinstalled) and ostensibly configured. It works great when I run manual backups, but it never runs automatically (either for full or incremental backups). I've tried a few other options (e.g., Backula, or the few others that show up in Synaptic), but -- mostly due to my status of "idiot" -- none of them have worked automatically. 

Since I'm replacing the NAS200 anyway, I hoped to get one pre-configured, if at all possible.

---

### Post by Locke_99GS on 2009-12-02
I'm unaware of any pre-configured (or otherwise have software for, included) NAS devices, but I wouldn't know anyways.

The one you got to function correctly when run manualy, can it be run from the command line? If so, just create a cronjob to do it for you and whatever interval and/or time you want.

---

### Post by Hospadar on 2009-12-02
I don't think anything is just going to work automatically, everyone wants different kinds of backups and I don't know of any backup softwares that even attempt to find some totally automatic setup.

As for softwares though, I loooove backup pc, it's got a great web interface, it's pretty easy to set up, it makes it really easy to restore or retrieve files from a backup.

---

### Post by suomalainen on 2009-12-02
Hi,

I know your looking for info on backing up your Linux machine but I had a 500GB WD MyBook World edition that I applied a hace to.

See:  [http://mybookworld.wikidot.com/hacks-and-howto](http://mybookworld.wikidot.com/hacks-and-howto)

Now I don't have to use the Mionet software anymore and can access MyBook from any web browser anywhere. I can even exchange mp3s and other files types. Somethinf the mionet and WD would not allow you to do.....

Regardless, I could not see why you could not just drag and drop the files into such NAS as this...

---

