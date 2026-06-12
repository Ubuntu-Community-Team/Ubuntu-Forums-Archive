---
title: "update problems"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by GLMantra663 on 2011-02-24
using ubuntu 10.10 on macbook pro 7,1 and for the past few days i've had  the "!" sign in my top bar (dont know what its called) telling me i need updates. so i run[I] 
sudo apt-get update[/I] in the terminal
and this is my feed back
[I]
W: Failed to fetch [http://ppa.launchpad.net/macte/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/macte/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/macte/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/macte/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

i just need to know how to either remove these from the sources list, or replace them with the up to date sources.
any takers?

---

### Post by thefasterblueone on 2011-02-25
To edit your sources.list run this command:

```
sudo gedit /etc/apt/sources.list
```

After editing the file click "File", "Save" then close.



Here are the correct URL's if you want to replace them.

[http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/maverick/main/source/Sources.gz)


[http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)


The part that is wrong is here,  [http://ppa.launchpad.net/](http://ppa.launchpad.net/)[COLOR="Red"]mactel[/COLOR]-support/......

---

