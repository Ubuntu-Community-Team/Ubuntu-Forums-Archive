---
title: "Lexmark Z615 / can't connect to keyserver"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by waggers on 2011-05-02
I have a Lexmark Z615 printer which has been working fine with Ubuntu 10.04, except for the last couple of days. It now prints about halfway down the page and stops; running the printing troubleshooter doesn't come up with any useful advice.

I'm assuming this is caused by some recent update or other (as we've made no changes to the system other than Update Manager's recommendations). However when update manager has been running it has been suggesting a partial distribution upgrade each time. Because of the printer problem I did some research and used sudo apt-get dist-upgrade yesterday. I no longer get the partial upgrade prompt, but when I check for updates I get a public key error:

```
GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
```

Reading up on this I've tried to download the public key using
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
```
and
```
gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 5A9A06AEF9CB8DB0
```
plus a variety of other attempts, including trying alternative keyservers as mentioned [here]("https://bugs.launchpad.net/ubuntu-website/+bug/435193/comments/14"), but always receive the same response:

```
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

I've also tried searching on the keyserver's web interface at [http://keyserver.ubuntu.com:11371/](http://keyserver.ubuntu.com:11371/) for 5A9A06AEF9CB8DB0 and F9CB8DB0 but get no results. I'm not sure if those are the right search terms, or what I'm supposed to do with the results if I did find any, but figured it was worth a shot.

I'm kind of working on the assumption that fixing the public key issue with update manager will lead to a fix for the printer, which is my primary concern, but may be barking up the wrong tree completely. Any help would be greatly appreciated.

---

### Post by waggers on 2011-05-02
As a last resort, is there a way to roll back the updates I've applied since Friday (when we last printed without problems)?

---

### Post by waggers on 2011-05-02
Ok, as it turns out the two things are not connected. The printer issue was actually something embarrassingly simple - either the USB cable connecting the printer to the PC had become slightly dislodged somehow or some dust had got in the way. Basically, [this thread]("http://ubuntuforums.org/showthread.php?t=1646235") inspired me to try plugging it into a different USB socket and suddenly the printer works fine again.

The keyserver issue is far from resolved and I doubt that will be sorted any time soon, judging by similar threads I've read on the subject, but as that wasn't my primary concern when I started the thread I'm going to mark this as solved.

---

