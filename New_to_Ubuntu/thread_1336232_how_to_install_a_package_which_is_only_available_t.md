---
title: "how to install a package which is only available to 9.10"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by zsero on 2009-11-24
I am using 8.04.3 but there is a package, (actually a lot of packages for ghci Haskell compiler) which are only available under 9.10. Is there a way to add 9.10 packages to 8.04 easily? The most important one would be the quickcheck2 dev library.

---

### Post by kansasnoob on 2009-11-24
Sometimes you can find the .debs here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

From there click on Karmic, then if I have no idea which section a package is in I just click on All Packages at the bottom of the page.

Just for instance I searched for libghc6-quickcheck2-dev and found this:

[http://packages.ubuntu.com/karmic/libghc6-quickcheck2-dev](http://packages.ubuntu.com/karmic/libghc6-quickcheck2-dev)

It lists the dependencies, recommendations, suggestions.

My mileage has varied greatly regarding success or failure. It's best to keep a list of what you install - if using Firefox the Downloads window does it for you - that way you can reverse things using Synaptic in case of total borkage.

Good luck!

---

### Post by snowpine on 2009-11-24
I Google'd "ghci Haskell compiler" for you and found this page:

[http://www.haskell.org/ghc/download_ghc_6_10_4.html](http://www.haskell.org/ghc/download_ghc_6_10_4.html)

It has instructions for installing in Ubuntu, as well as the source you can use to compile it yourself.

---

### Post by slakkie on 2009-11-24
> **snowpine said:**
> I Google'd "ghci Haskell compiler" for you and found this page:

[http://www.haskell.org/ghc/download_ghc_6_10_4.html](http://www.haskell.org/ghc/download_ghc_6_10_4.html)

It has instructions for installing in Ubuntu, as well as the source you can use to compile it yourself.

If you compile it from source, make sure you have the checkinstall package installed first. Then when you install ghc, run sudo checkinstall make install instead of just sudo make install. That way it will be added as a Debian/Ubuntu package.

---

