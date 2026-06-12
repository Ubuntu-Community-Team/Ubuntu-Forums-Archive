---
title: "Compiling from source via synaptic"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by tpapastylianou on 2009-07-21
I was wondering if there is a way to install a program by compiling it from source, as opposed to installing the precompiled binary, but by using synaptic? 

Or even, simply if there is a way to obtain source code using synaptic?

I ask this, because I noticed that synaptic->repositories includes a tickbox for enabling sourcecode downloads, but I don't see an obvious way of downloading a program's source file using synaptic. Am I missing something?

I know there are console options, such as:
- using apt-build: [sudo apt-build install package]
or 
- using apt-get:
   - step 1: [sudo apt-get build-dep package]
   - step 2: [apt-get -b source package], or [apt-get source package] followed by [dpkg-buildpackage -rfakeroot -uc -b], which creates a .deb file.
   - step 3: [sudo dpkg -i package.deb] on the created .deb file to install to the system.

but I was wondering if there's a way to do the above with synaptic :)

If not, it would be great if this functionality was considered for future versions of synaptic (possibly by invoking apt-build in the background?). I.e., where you click to install a program, to have another few options, such as 'download source' and 'compile from source' or something along those lines. (gentoo people always rant about their portage and their completely optimized systems :p )

PS. To preempt any 'why not just use console' replies, there are advantages and disadvantages to console vs gui methods. I'm just asking if there's an equivalent gui / synaptic method, and if there isn't one, I'm pointing out it would be useful and desirable. :)

---

### Post by koleoptero on 2009-07-21
By enabling the source code downloads you can just download the source code of a program through synaptic, not actually compile it.

But I don't know if there are any gui clients that can do what you want.

---

### Post by Mark Phelps on 2009-07-21
Basically ... no.  Synaptic is a package management system, and that includes source packages as well as binary. The providers of source code generally include the configure, make, and build scripts with their source code.  The variations are too great to expect package management to include this as well.

---

