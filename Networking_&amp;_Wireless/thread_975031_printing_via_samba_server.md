---
title: "printing via samba server"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by aaronp on 2008-11-08
Hi all,

I am running Ubuntu 8.04.01 on my desktop with a Canon IP3300 printer connected locally.
My partner has a laptop running Vista which I have enabled to access the Ubuntu file system and also the printer (raw via CUPS) with a Samba server.
We have no issues accessing files over the network connection and also at times have had no issues printing. Press print on Vista, almost immediately the printer fires up and out it comes!

The issue we are having is that intermittently (and ever more frequently) we try to print something via the Samba/CUPS setup from the Vista laptop and the printer status (in Vista) simply says 'collecting printer status' forever - until you cancel the job.
It appears that if you restart the Ubuntu PC AND the Vista laptop it will most likely (but not always) print fine like normal when they both boot up again.

Any ideas on what the issue might be?

thanks
Aaron

---

### Post by vaadoo on 2008-11-08
I am in a similar situation, but I haven't reached as far as you have.
I have a desktop Ubuntu & a laptop running on vista home premium.  How did you set up  File/Print sharing?  I can access the printer using when I have booted into the linux partition of the laptop, but not from the vista partition.  
Can you guide me little bit?

---

### Post by aaronp on 2008-11-08
Sure, I'll see what I can do.
I think I followed a guide pretty closely to set this up so my actual understanding of it may not be as good as I think!

Here is the [printers] section of my smb.conf:

```

[printers]
  browseable = yes
  printable = yes
  public = yes
  create mode = 0700
  guest only = yes
  use client driver = yes
  path = /tmp

```

and the relevant lines in the global section:

```

	security = user
	  printcap name = cups
	  printing = cups

```

I think the 'use client driver' is the key because it allows the remote PC to access the pinter directly, without trying to use my linux printer drivers to print.
So then in Vista, browsing the Samba server should show a printer as one of the options. (I think you need to restart the Samba service when you update the smb.conf file)
You can select to use this printer and then you can install it as if it was a local printer, by downloading (or using CD) to install the appropriate drivers locally - but set to work with the remote printer.

Hope this help - I set it up a long time ago now so can't remember if I had to alter my cups configuration at all....sorry.

Aaron

---

