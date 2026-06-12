---
title: "Error with Software Download Centre"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by CollyMcK on 2011-01-27
Hi Guys,
 
I am just coming back to Linux - studied it in Uni for a module but havent used it in a while.  I got Ubuntu running fine on my Sony Vaio laptop.  I went to a wesite to find ten best programs to download.  I ran into an error with the first and tried to do a kill on the get/apt process i think it was.  I then tried to kill some root processes and tried a restart but my software centre is still not working correctly.
 
I have attached a print screen of the message I am getting.  Can anyone help me resolve this.  If not would my best option be to format the partition i put linux on and re-install it as I really want to be using it.
 
Thanks for any help.
 
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by oldos2er on 2011-01-27
Can you open a terminal (Applications, Accessories, Terminal) and run the following command: ```
sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
``` and if there are any errors, copy and paste them here.

---

### Post by CollyMcK on 2011-01-27
oldos2er - Many Thanks for your help.  It came when i was doing a sudo apt get restricted extras yesterday.  However its comes to the same screen as I have showed you below - I am not sure how to OK this screen - can you provide any guidance.

Colly (Ireland)

---

### Post by mharrison on 2011-01-27
> **CollyMcK said:**
> oldos2er - Many Thanks for your help.  It came when i was doing a sudo apt get restricted extras yesterday.  However its comes to the same screen as I have showed you below - I am not sure how to OK this screen - can you provide any guidance.

Colly (Ireland)

I believe if you click inside the window and hit the TAB key you can get the OK to highlight in red and then hit the spacebar or the enter key.

---

### Post by CollyMcK on 2011-01-27
Hey - Many Thanks - Embarrassed face for not figuring this out...lol

---

