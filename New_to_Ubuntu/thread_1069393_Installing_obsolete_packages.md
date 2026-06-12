---
title: "Installing obsolete packages"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2009-02-13
I need to use g++-3.4 (I have g++-4.3 installed currently). 

apt-get says "Package g++-3.4 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source"

What repositories must I enable to be able to install old/obsolete packages?

Thanks.

---

### Post by Temposs on 2009-02-13
It looks like it's not in the Ubuntu repositories in Ubuntu 8.10. You could try to find it on the web manually, if you need it:

[http://packages.ubuntu.com/dapper/i386/g++-3.4/download](http://packages.ubuntu.com/dapper/i386/g++-3.4/download)

That should be it. You can download it directly or add the repository for dapper, as it indicates on that page.

---

### Post by Eto_Demerzel on 2009-02-13
Thanks. But using Synaptic didn't work for me.

I got it done manually from [this thread]("https://bugs.launchpad.net/ubuntu/+source/gcc-3.4/+bug/295427").

From the last post in the above thread.

---

