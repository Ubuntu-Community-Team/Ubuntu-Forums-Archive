---
title: "Ubuntu 10.04 - Rhythmbox not working"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Kangaroo_Style on 2010-04-30
Just tried to open Rhythmbox, and it wouldn't open up. Went to the terminal and typed 'rhythmbox' and received the message, "error while loading shared libraries: libtotem-plparser.so.12: cannot open shared object file: No such file or directory"

I then went into Synaptic Packet Manager, and I found that I already have "libtotem-plparser17" installed. There wasn't a "libtotem-plparser.so.12" in Synaptics. 

Any ideas on how I can fix this problem?

---

### Post by Kangaroo_Style on 2010-05-01
bump

---

### Post by warrewards.com on 2010-05-01
> **Kangaroo_Style said:**
> Just tried to open Rhythmbox, and it wouldn't open up. Went to the terminal and typed 'rhythmbox' and received the message, "error while loading shared libraries: libtotem-plparser.so.12: cannot open shared object file: No such file or directory"

I then went into Synaptic Packet Manager, and I found that I already have "libtotem-plparser17" installed. There wasn't a "libtotem-plparser.so.12" in Synaptics. 

Any ideas on how I can fix this problem?

Here's a temporary hackaround, tho as of yet, I'm not able to get the portable music players plugin to work.

Open a terminal

run this:

sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.12

rhythmbox will at least run like this.

Again, not sure whether this will cause other problems. I've only been messing around with it for 10 minutes or so.


-- Jeremy

---

### Post by hellocatfood on 2010-05-02
Do you know if there's a bug report open about this?

---

### Post by Kangaroo_Style on 2010-05-02
> **warrewards.com said:**
> Here's a temporary hackaround, tho as of yet, I'm not able to get the portable music players plugin to work.

Open a terminal

run this:

sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.12

rhythmbox will at least run like this.

Again, not sure whether this will cause other problems. I've only been messing around with it for 10 minutes or so.


-- Jeremy


Thank you that worked.

Could you explain what occurred? I understood you copied the libtotem-plparser.so to the folder. But not sure what else happened.



> **hellocatfood said:**
> Do you know if there's a bug report open about this?

Not that I know of, I don't know how to check though.

---

### Post by warrewards.com on 2010-05-02
> **Kangaroo_Style said:**
> Thank you that worked.

Could you explain what occurred? I understood you copied the libtotem-plparser.so to the folder. But not sure what else happened.





Not that I know of, I don't know how to check though.
Basically it was looking for a non-existent file. What we did was copy a newer version of that file to the location it was looking for the older one. Although I'm peeved that I can't get my iPod working with it. :(

---

### Post by Mike Bates on 2010-05-13
[SIZE="3"]I tried your advice and get the error:[/SIZE]

cp: cannot stat `/usr/lib/libtotem-plparser.so': No such file or directory

[SIZE="3"]When I try to start in a terminal I get the error:[/SIZE]

(rhythmbox:26290): Rhythmbox-WARNING **: Could not open device /dev/radio0
** (rhythmbox:26290): DEBUG: Loading the real store page

** (rhythmbox:26290): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3Dc_xDEWw6pEJ05wbznr9FOmhz%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1273744388%26oauth_token%3DdhW0cTjnWdKMfT2wDgXn%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&CbShFkGncvC9pHHDllQn4wG43c26KW6Sw2KGDjXXdvPWGTSsKL4S8MSVfLchQg6Q7f2Nmz8mZgPS9p5p'

** (rhythmbox:26290): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=c_xDEWw6pEJ05wbznr9FOmhz&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273744388&oauth_token=dhW0cTjnWdKMfT2wDgXn&oauth_verifier=None&oauth_version=1.0&oauth_signature=33%2F8tu3fpCkryAws9UzSY7Dy04U%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=c_xDEWw6pEJ05wbznr9FOmhz&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273744388&oauth_token=dhW0cTjnWdKMfT2wDgXn&oauth_verifier=None&oauth_version=1.0&oauth_signature=33%2F8tu3fpCkryAws9UzSY7Dy04U%3D)
Segmentation fault

[SIZE="3"]Any suggestions?[/SIZE]

---

### Post by kevinatkins on 2010-05-13
This is bizarre. My rhythmbox is working fine, so I decided to see what libraries it's using using, see if I could throw some light on it for you guys..

According to my installation the version of libtotem-plparser is as below -

libtotem-plparser.so.17 => /usr/lib/libtotem-plparser.so.17

Which suggests that your Rhythmbox is looking for the wrong version of the library.... Is your Ubuntu installation an upgrade from a previous release?

---

### Post by Mike Bates on 2010-05-14
> **kevinatkins said:**
> This is bizarre. My rhythmbox is working fine, so I decided to see what libraries it's using using, see if I could throw some light on it for you guys..

According to my installation the version of libtotem-plparser is as below -

libtotem-plparser.so.17 => /usr/lib/libtotem-plparser.so.17

Which suggests that your Rhythmbox is looking for the wrong version of the library.... Is your Ubuntu installation an upgrade from a previous release?

I did the online upgrade to 10.04, however, the file you list is in the folder you suggest. I still get the error I previously listed.
Maybe I should do a complete remove of Rhythmbox and re install it. What do you think?

---

### Post by kevinatkins on 2010-05-14
Yes, try doing a reinstall of Rhythmbox - it certainly looks like the problem is with Rhythmbox itself, rather than another part of your system..

---

### Post by GSF1200S on 2010-05-14
```
sudo apt-get purge rhythmbox
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install rhythmbox rhythmbox-plugins
```

The dpkg and -f command shouldnt be necessary, but considering you are having issues with a package, I list them just to be safe. After you run these commands, ensure that rhythmbox is version 0.12.8. :)

---

### Post by Mike Bates on 2010-05-14
I had tried to re-install through Synaptic Package Manager, with no luck. I have since removed it using Ubuntu Software Centre and then re-installing it, it now works!
Cheers for your help.

---

### Post by edo152 on 2010-05-16
Reinstallation with Synaptics Package Manager worked for me.

---

### Post by koolerking on 2010-05-26
Purge and re install via terminal worked for me as well.

Cheers
:guitar:

---

