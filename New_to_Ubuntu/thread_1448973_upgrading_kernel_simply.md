---
title: "upgrading kernel simply"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by lawrencegoodman on 2010-04-07
i am using lucid with kernel 2.32.xx
 
i have an hp l2105tm monitor though and apparently 2.34.xx has a driver to support it.
 
is there a simple noobie way to upgrade the kernel?
how much instability do i risk by doing this?

---

### Post by snowpine on 2010-04-07
The advice you received sounds suspicious. :) The kernel doesn't control your monitor--your graphics card does--and kernel 2.6.34 hasn't been released yet anyways. 

What exactly are the problems you're currently experiencing with your monitor? What kind of graphics card does your computer have, and have you installed any drivers for it?

---

### Post by undecim on 2010-04-07
> **snowpine said:**
> The advice you received sounds suspicious. :) The kernel doesn't control your monitor--your graphics card does--and kernel 2.6.34 hasn't been released yet anyways. 

What exactly are the problems you're currently experiencing with your monitor? What kind of graphics card does your computer have, and have you installed any drivers for it?

I think he's referring to multi-touch capabilities. [http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/382087-382087-64283-3181050-3181048-4031739.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/382087-382087-64283-3181050-3181048-4031739.html)

The only way I know of upgrading the kernel past what's in the Ubuntu repositories is to compile it yourself.

---

### Post by snowpine on 2010-04-07
Cool! I want one. :)
Post back if you have any luck getting it to work.

ps you can get the kernel here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
but as I said, it is still a "release candidate" so I do not recommend it.

---

### Post by Bachstelze on 2010-04-07
> **undecim said:**
> 
The only way I know of upgrading the kernel past what's in the Ubuntu repositories is to compile it yourself.

Not anymore. ;) The Ubuntu kernel team has an archive of packaged kernels at [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by undecim on 2010-04-07
> **Bachstelze said:**
> Not anymore. ;) The Ubuntu kernel team has an archive of packaged kernels at [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Oooh, very useful. Thanks.

---

### Post by lawrencegoodman on 2010-04-07
Thanks for the advice.

---

