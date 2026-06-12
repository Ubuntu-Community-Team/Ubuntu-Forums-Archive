---
title: "Broken Filter"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-11-10
I keep getting broken packages errors so I used the directions below to fix it
[http://srikanthkabadi.blogspot.com/2010/02/solution-for-update-manager-broken.html#comment-form]("http://srikanthkabadi.blogspot.com/2010/02/solution-for-update-manager-broken.html#comment-form")

Then I get this different error message from synaptic,please help me resolve this

```
E: /var/cache/apt/archives/libtracker-client-0.9-dev_0.9.26-0ubuntu0~unstable0.10.10.1_i386.deb: trying to overwrite '/usr/share/gtk-doc/html/libtracker-client/libtracker-client-Resources.html', which is also in package libtracker-client-0.8-dev 0.8.17-0ubuntu1
E: /var/cache/apt/archives/libtracker-miner-0.9-dev_0.9.26-0ubuntu0~unstable0.10.10.1_i386.deb: trying to overwrite '/usr/share/gtk-doc/html/libtracker-miner/libtracker-miner.html', which is also in package libtracker-miner-0.8-dev 0.8.17-0ubuntu1


```

---

### Post by sikander3786 on 2010-11-10
Simply try this command from terminal.

```
sudo apt-get clean
```

---

### Post by cmcanulty on 2010-11-10
Then I get this error after
```
W:Failed to fetch http://ppa.launchpad.net/THE_PPA/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/THE_PPA/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sikander3786 on 2010-11-10
> **cmcanulty said:**
> Then I get this error after
```
W:Failed to fetch http://ppa.launchpad.net/THE_PPA/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/THE_PPA/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```
Means the old error is gone?

This 404 error means that the server for your custom added repositories is not responding. Go to Software Center > Edit > Software Source > Other Software tab and disable any Launchpad ppas and try again.

Hope there are no errors this time :-)

---

### Post by cmcanulty on 2010-11-10
OK thanks I did that. I guess it doesn't seem like a good idea to uncheck maverick main as then won't I get the updates I should for maverick? And yes original error message is gone.

---

### Post by plucky on 2010-11-11
> **cmcanulty said:**
> OK thanks I did that. I guess it doesn't seem like a good idea to uncheck maverick main as then won't I get the updates I should for maverick? And yes original error message is gone.

Read the error message

That is not Maverick Main it is a launchpad PPA and should be located in the "other Software" tag in Software Sources.

---

### Post by cmcanulty on 2010-11-12
Oh thanks I never knew that

---

### Post by srikanth.gundaz on 2010-11-24
Goto terminal and type 
**sudo apt-get install -f**

This will fix broken filters and packages :D:)
Thank you :)

---

### Post by cmcanulty on 2010-11-24
Thanks, very helpful!

---

