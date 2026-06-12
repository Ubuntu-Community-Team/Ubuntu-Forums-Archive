---
title: "rhthymbox bug"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by wobwill on 2010-05-06
I am unable to run rhythmbox. This is the code I get from the terminal.

Please help

william@william-eee:~$ rhythmbox
** (rhythmbox:1764): DEBUG: Loading the real store page
** (rhythmbox:1764): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
Segmentation fault
william@william-eee:~$ 

Many Thanks

Will

---

### Post by -humanaut- on 2010-05-06
Does it run without an Internet Connection?

---

### Post by dearingj on 2010-05-06
I've had a similar problem, until recently. Here's the solution that worked for me:

1) Open up the program gconf-editor (not shown in the applications menu by default, so you'll have to run it from a terminal)
2) In gconf-editor, navigate to the folder /apps/rhythmbox/plugins/mtpdevice
3) With the mtpdevice folder selected, you should see in the right pane an entry called 'active' with a checkbox; uncheck it.
4) Close gconf-editor and start rhythmbox

If rhythmbox still doesn't open, try disabling other plugins in the same way.

---

### Post by wobwill on 2010-05-06
Hi Humanaut

No

terminal output

william@william-eee:~$ rhythmbox
** (rhythmbox:2182): DEBUG: Loading the real store page

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DAVtRmYNYujvuHh1Rwf4v6SsWoCEy%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1273175923%26oauth_token%3DFsQzxgN0L1VJCQw9qjRS%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&RxqXrnQxzNNXGpvJVJ5sn35l9MB22sGVzRh3hD15R7tQCLrLDLbJXzHTd6HbSzq6Dx0dS7lC6d39fKR5'

** (rhythmbox:2182): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=AVtRmYNYujvuHh1Rwf4v6SsWoCEy&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273175923&oauth_token=FsQzxgN0L1VJCQw9qjRS&oauth_verifier=None&oauth_version=1.0&oauth_signature=2HQhr95e9MsoVUz3HlLhEazh19o%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=AVtRmYNYujvuHh1Rwf4v6SsWoCEy&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273175923&oauth_token=FsQzxgN0L1VJCQw9qjRS&oauth_verifier=None&oauth_version=1.0&oauth_signature=2HQhr95e9MsoVUz3HlLhEazh19o%3D)
Segmentation fault
william@william-eee:~$ 

Hope this helps

I have also just set up an Ubuntu One account. I'll see if that helps and post.

Will

---

### Post by wobwill on 2010-05-06
Have tried to start Rhythmbox with an internet connection and ubuntu one account set up.

Here is my terminal output:

william@william-eee:~$ rhythmbox
** (rhythmbox:2182): DEBUG: Loading the real store page

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DAVtRmYNYujvuHh1Rwf4v6SsWoCEy%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1273175923%26oauth_token%3DFsQzxgN0L1VJCQw9qjRS%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&RxqXrnQxzNNXGpvJVJ5sn35l9MB22sGVzRh3hD15R7tQCLrLDLbJXzHTd6HbSzq6Dx0dS7lC6d39fKR5'

** (rhythmbox:2182): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=AVtRmYNYujvuHh1Rwf4v6SsWoCEy&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273175923&oauth_token=FsQzxgN0L1VJCQw9qjRS&oauth_verifier=None&oauth_version=1.0&oauth_signature=2HQhr95e9MsoVUz3HlLhEazh19o%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=AVtRmYNYujvuHh1Rwf4v6SsWoCEy&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273175923&oauth_token=FsQzxgN0L1VJCQw9qjRS&oauth_verifier=None&oauth_version=1.0&oauth_signature=2HQhr95e9MsoVUz3HlLhEazh19o%3D)
Segmentation fault
william@william-eee:~$ rhthymbox
rhthymbox: command not found
william@william-eee:~$ rhythmbox
** (rhythmbox:2418): DEBUG: Loading the real store page

** (rhythmbox:2418): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3D2EZ99_jZeQVDjY9XDiID6VYdc0a1%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1273176209%26oauth_token%3DFsQzxgN0L1VJCQw9qjRS%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&RxqXrnQxzNNXGpvJVJ5sn35l9MB22sGVzRh3hD15R7tQCLrLDLbJXzHTd6HbSzq6Dx0dS7lC6d39fKR5'

** (rhythmbox:2418): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=2EZ99_jZeQVDjY9XDiID6VYdc0a1&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273176209&oauth_token=FsQzxgN0L1VJCQw9qjRS&oauth_verifier=None&oauth_version=1.0&oauth_signature=JavOM4VPN4KNNvd6Wgd3BiCmJNU%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=2EZ99_jZeQVDjY9XDiID6VYdc0a1&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273176209&oauth_token=FsQzxgN0L1VJCQw9qjRS&oauth_verifier=None&oauth_version=1.0&oauth_signature=JavOM4VPN4KNNvd6Wgd3BiCmJNU%3D)
Segmentation fault
william@william-eee:~$ 

Many Thanks in advance

Will

PS - I've set up a samba share with a winxp machine. I am a noob with Linux, but this appears to be working. Could this cause a conflict? If so how do I check?

---

### Post by sandyd on 2010-05-06
[[s]https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/550048[/s]]("https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/550048")
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/569481](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/569481)

---

### Post by Nightstrike2009 on 2010-05-06
I use Banshee instead, why not try that instead? Banshee seems a lot better in my opinion :-)

PS: may Have to download banshee.deb from main repo on an american mirror the gb one seems to hang at 78% for some reason. site located here [http://packages.ubuntu.com/lucid/i386/banshee/download]("http://packages.ubuntu.com/lucid/i386/banshee/download")

---

### Post by wobwill on 2010-05-06
Carlee - thank you. I'll add a crash report to this bug.

dearingj - thank you. I've tried your solution, but can't get it to work on my machine.

---

### Post by wobwill on 2010-05-06
Nightstrike - the simplest solution is often the best. Many Thanks.

---

### Post by lidex on 2010-05-06
Have you tried this terminal command:
```
sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.12

```

---

