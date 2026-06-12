---
title: "re-installing jackd"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by gorgon on 2009-08-29
hi all!

I just upgraded to jaunty. While I was in intrepid I had some issues with jackd (with a very old version as the only one packaged for intrepid) so I made some effort to install it from source, but I had to manually move the jackd binary file to the bin directory to make it work.

Now, in Jaunty, there's a newer verion of jackd supported which I'd like to use, and I thought it would just overwrite the version I installed when it was upgrading, but apparentry not since it's not working.

So, Im trying to remove it and install it again.
apt-get remove jackd
gives me this:

```

The following packages will be REMOVED:
  ardour bitmeter bitscope freqtweak jack-rack jack-tools jackd jamin
  meterbridge qjackctl timemachine
0 upgraded, 0 newly installed, 11 to remove and 1 not upgraded.
After this operation, 18.4MB disk space will be freed.

```

is it safe to remove? it seems strange since Ardour is a lot more than 18.4MB.. is it just a way of saying that these programs depend on jackd?

thanks!
g

---

### Post by NoaHall on 2009-08-29
Yes, it's fine to uninstall, when you install again, all these will be added right back.

---

### Post by gorgon on 2009-08-29
thanks! works just fine.

---

