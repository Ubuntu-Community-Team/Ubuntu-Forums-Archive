---
title: "bluetooth mouse"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by Bowjangles on 2007-11-24
So I've already done some research and I added my dell blutooth mouse's mac address to  /etc/bluetooth/hcid.conf

I was also able to connect the mouse using: sudo hidd --search
But now I can't get it to auto connect when I turn it on. The forum post I found told me to edit this file: sudo gedit /etc/default/bluez-utils
but when i enter that command it opens up a blank file. I'm running ubuntu gutsy. Any ideas?

Thanks in advance.

Edit :: I feel stupid, I figured it out by trying different file names. I found it under 
sudo gedit /etc/default/bluetooth

Just change 

HIDD_ENABLED=0
HIDD_OPTIONS="--master --server"

to

HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"

Hope this helps anyone who needs it.

---

