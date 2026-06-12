---
title: "Is there a limit to how fast you can download from the repos?"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by CharlesA on 2011-01-11
Hi,

I recently upgraded my internet and it seems like I am not downloading from the regular ubuntu repos as fast as I did. Before I'd get about 200K/sec, now it's usually hovering between 80K/sec and 120K/sec. My connection is capable of 1.5MB/sec down, and I'm obviously not reaching it.

Downloads from thirdparty repos (virtualbox, etc) go full speed.

Is there a setting that needs changing or something?

I'm using Ubuntu Server 10.04.1. :)

Thanks.

---

### Post by bodhi.zazen on 2011-01-12
You could try this 

[http://www.webupd8.org/2009/11/improve-apt-get-install-and-upgrade.html](http://www.webupd8.org/2009/11/improve-apt-get-install-and-upgrade.html)

---

### Post by CharlesA on 2011-01-12
Thanks Bodhi.

I was also looking at using a different mirror as well, but I run into the problem of not having synaptic or update manager installed as this is a headless server.

Almost all the stuff I found on that were directions on how to do it the "GUI way"

---

### Post by mastablasta on 2011-01-12
also transmission is measured in megabits not megabytes, so if you calculate correctly... although getting less is a bit strange.

---

### Post by garvinrick4 on 2011-01-12
List of mirrors.

[https://edge.launchpad.net/ubuntu/+archivemirrors](https://edge.launchpad.net/ubuntu/+archivemirrors)

---

### Post by CharlesA on 2011-01-12
> **mastablasta said:**
> also transmission is measured in megabits not megabytes, so if you calculate correctly... although getting less is a bit strange.

Yeah, I know. :) I was going off of what it says when it's doing downloads.

> **garvinrick4 said:**
> List of mirrors.

[https://edge.launchpad.net/ubuntu/+archivemirrors](https://edge.launchpad.net/ubuntu/+archivemirrors)

Thanks for the link! It looks like they have a list of sources.list too.

---

