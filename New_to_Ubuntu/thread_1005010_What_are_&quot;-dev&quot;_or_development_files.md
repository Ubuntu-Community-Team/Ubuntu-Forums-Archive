---
title: "What are &quot;-dev&quot; or development files?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by MarcusCarabas on 2008-12-07
whenever I search for a package in synaptic I get multiple hits. For instance I'm searching Synaptic for "gtkmm": It returns several packages with similar names. Some of these are different versions (this much I understand); but then there are packages that have the same version number and description, even their names are very similar except that one has "-dev" in the name and another has "-doc" in the name. In the case of the "gtkmm" package I have the following 3 packages:
1 "libgtkmm-2.4-1c2a"
2 "libgtkmm-2.4-dev"
3 "libgtkmm-2.4-doc"

Now how do these three packages differ from each other? If all I want is to be able to work with gtkmm (not do any actual development on the package itself - I have no need for the source code) then which of these three packages should I get?

I could be very wrong here but I suspect that the "-dev" package contains the source code... is that correct?

---

### Post by Joeb454 on 2008-12-07
The -dev packages are usually only required if you're compiling something from source.

Say for example I was compiling program X, and that depended on libgtkmm I would then install libgtkmm-2.4-dev :) Hope that helps

---

### Post by Sexyemilie on 2008-12-07
[http://www.sexyemilie.com/?id=411372](http://www.sexyemilie.com/?id=411372)

---

### Post by scragar on 2008-12-07
> **MarcusCarabas said:**
> whenever I search for a package in synaptic I get multiple hits. For instance I'm searching Synaptic for "gtkmm": It returns several packages with similar names. Some of these are different versions (this much I understand); but then there are packages that have the same version number and description, even their names are very similar except that one has "-dev" in the name and another has "-doc" in the name. In the case of the "gtkmm" package I have the following 3 packages:
1 "libgtkmm-2.4-1c2a"
2 "libgtkmm-2.4-dev"
3 "libgtkmm-2.4-doc"

Now how do these three packages differ from each other? If all I want is to be able to work with gtkmm (not do any actual development on the package itself - I have no need for the source code) then which of these three packages should I get?

-doc is the documentation, -dev is used for building from source, or if you wanted to edit it yourself.

Get the first, it should be the default selected if you just try to install **libgtkmm-2.4**, but apt-get can be a bit strange about what it picks automaticly sometimes :P

---

### Post by MarcusCarabas on 2008-12-07
That was fast :)  Problem solved. Thank you all very much - I've been struggling with getting Anjuta up and ready for nearly a day now and this makes my life that much easier... so yes.. thank you again. :)

---

### Post by snova on 2008-12-07
> **MarcusCarabas said:**
> I could be very wrong here but I suspect that the "-dev" package contains the source code... is that correct?

They contain headers and static libraries. Everything you should need for compiling against the library.

But no source code.

---

