---
title: "How do I install Ubuntu on an Ext HD without screwing up the MBR on my internal drive"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by skew on 2010-11-25
How does one install Ubuntu on a external hard drive without making a mess out of the MBR on my laptops internal hard drive?  

  My current laptop is new and has Win7-64 on it. While I test out this new laptops ability to work well with Ubuntu I would prefer not to install Ubuntu on that internal drive. I would also prefer not to have to remove the laptops HD in order to install ubuntu effectively on my external HD.

  In the past I've made a mess out of my grub and/or MBR by acting first withoput knowing about the ramifications of installing without forethought of the possible consequences.  

  Is this possible? Remember I can't mess with the MBR currently on the laptops's HD. 

  I don't want to have to have the external drive connected in order to boot into the lapto, etc.

Thx all!

---

### Post by jtarin on 2010-11-25
During the installation process there is a step where you choose to install Grub. Install it to your external hardrive and then look to my signature refering to EasyBCD to use the Windows loader to boot Ubuntu. If you need more exacting info please feel free to PM me with your email address and I can send you the info you need.However it will be some hours before I can as I am at work now and my install instructions are at home.

---

### Post by skew on 2010-11-25
> **jtarin said:**
> During the installation process there is a step where you choose to install Grub. Install it to your external hardrive and then look to my signature refering to EasyBCD to use the Windows loader to boot Ubuntu. If you need more exacting info please feel free to PM me with your email address and I can send you the info you need.However it will be some hours before I can as I am at work now and my install instructions are at home.


Thanks for the reply Jtarin.

I will look at the URL you referred to. I'll be in touch if I see a need to.  

As I mentioned earlier if EasyBCD does not mess with my laptops MBR I'll be happy.

Cheers!

---

### Post by wilee-nilee on 2010-11-25
> **skew said:**
> Thanks for the reply Jtarin.

I will look at the URL you referred to. I'll be in touch if I see a need to.  

As I mentioned earlier if EasyBCD does not mess with my laptops MBR I'll be happy.

Cheers!

To be honest the MBR is easy to fix. The only advantage esybcd2 will give here is provide a boot with your internal MBR for the external. If you want to boot the external use grub2 in the external MBR, and identify the distro and we will get you setup.

Jtarin just loves esybcd2 so that is where they go nothing wrong with that except for any kind of quick help on this forum if something goes wrong you will wait a long time for it. All the key daily helpers in boot problems are only slightly familiar with easybcd, the reason being is it is hardly ever really needed to be honest.

> **jtarin said:**
> During the installation process there is a step where you choose to install Grub. Install it to your external hardrive and then look to my signature refering to EasyBCD to use the Windows loader to boot Ubuntu. If you need more exacting info please feel free to PM me with your email address and I can send you the info you need.**However it will be some hours before I can** as I am at work now and my install instructions are at home.

Here is a example grub2 will install to the external MBR why is another program needed on top of this when the external will boot without it. Also note the highlights, if you want fast knowledgeable fixes, then avoid easybcd. This user knows it quite well but do you want to wait for one person out of over 50,000 regular users, this is well kookie thinking in my book.;)

---

