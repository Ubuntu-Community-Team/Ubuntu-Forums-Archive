---
title: "How to setup dual monitors in lucid?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by shebaw on 2010-05-05
Hi I have updated to lucid today and the opensource driver is better than the ati proprietary drivers. Setting up dual monitors using the ati catalyst drivers was easy, but I don't know how to do it on the default driver. Any suggestions will be appreciated.

P.S I tried installing the 10.04 catalyst driver but it wasn't good on performance and I had to uninstall it to get back to the default open source driver.

---

### Post by Troublegum on 2010-05-05
As far as I know (I use the nvidia close source driver personally), you have to use randr for that. Theres a graphical interface called grandr for that task that can be installed from the repositories.

---

### Post by shebaw on 2010-05-05
> **Troublegum said:**
> As far as I know (I use the nvidia close source driver personally), you have to use randr for that. Theres a graphical interface called grandr for that task that can be installed from the repositories.
 
Thank you verymuch, I will try it out tomorrow and update you my result. It will be a great relief if it works.

---

### Post by Calash on 2010-05-05
The catalyst control panel should be under System>Preferences.

If not you should be able to start it from the terminal

```

gksu amdcccle

```

I was able to easily setup my dual LCD's here.

---

### Post by shebaw on 2010-05-05
> **Calash said:**
> The catalyst control panel should be under System>Preferences.

If not you should be able to start it from the terminal

```

gksu amdcccle

```

I was able to easily setup my dual LCD's here.

Like I said on my post, I removed the proprietary driver because the open source driver for ati in 10.04 is way better than the catalyst driver. Thats why I'm looking for other options.

---

### Post by shebaw on 2010-05-05
Troublegum, yup your solution worked flawlessly. I can't thank you enough! You saved my day (heck, my linux installation!)

Thanks again!

---

### Post by donnyw on 2010-05-26
I believe I'm in a similar situation. I'm using the open drivers for my ATI Radeon 2400, but I haven't been able to make dual monitors work. Ubuntu only sees a single monitor (same with grandr). I have no idea how to get it to see that I have two monitors plugged in.

Not sure if it has anything to do with the problem, but this particular card has a single physical output with a plug that allows two monitors to be attached. This wasn't a problem in either 9.04 or 9.10.

---

### Post by shebaw on 2010-05-27
> **donnyw said:**
> I believe I'm in a similar situation. I'm using the open drivers for my ATI Radeon 2400, but I haven't been able to make dual monitors work. Ubuntu only sees a single monitor (same with grandr). I have no idea how to get it to see that I have two monitors plugged in.

Not sure if it has anything to do with the problem, but this particular card has a single physical output with a plug that allows two monitors to be attached. This wasn't a problem in either 9.04 or 9.10.

grandr solved my problem, too bad it's not working for you. Anyways, you could give the proprietary drivers a try(you can download them from the AMD website) and the Catalyst Control panel let's you set up multiple monitors.

---

