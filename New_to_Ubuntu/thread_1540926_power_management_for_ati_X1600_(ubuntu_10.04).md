---
title: "power management for ati X1600 (ubuntu 10.04)"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by crypticlynx on 2010-07-28
Hi!

Im new to ubuntu and I am basically in search for something similar to Powerplay under windows. Currently my driver is radeon.

I have done some google research and it seems that I have to edit the Xorg.conf file. This unfortunately doesnt exist. In another thread it was advised to create it with
```
 sudo Xorg - configure 
```But testing it via:
```
 X -config /home/username/xorg.conf.new 
```resulted in an error.

Are there any advices to solve the problem?

PS: before executing sudo "sudo Xorg - configure" I changed to the shell with "crtl+alt+F1" and used the command "sudo service gdm stop"

---

### Post by clhsharky on 2010-07-28
crypticlynx

Welcome to Ubuntu forum

Which card do you have the ATI Mobility Radeon X1600 or the ATI Radeon X1600 card?

> I have done some google research and it seems that I have to edit the Xorg.conf file. This unfortunately doesnt exist. In another thread it was advised to create it
Yes - In Ubuntu we can use the same functions as in Powerplay but we use the xorg.cofig file to do it.

I have used PM with these cards in Karmic and Lucid installs that I still have, but I'm on Maverick at the moment. Ill need to find my config and commands to help you. I cant remember every thing any more.

Also what functions were you wanting?

Sharky

---

### Post by crypticlynx on 2010-07-29
I'm using ubuntu on my laptop so I think it has to be the mobility version of the card.

The functions I want are all functions that deal with powersaving, because the fan of my laptop really annoys me. I kind of regret having bought a notebook with a dedicated graphics card...

Also I have heard that there is something called kernel mode-setting (KMS) or user-space  mode-setting (UMS), where KMS needs a newer kernel than the one lucid is shipped with (2.6.32-24-generic). Would it be worth to try to install that kernel?

Will it be possible to reach the same power saving as under windows?

---

### Post by crypticlynx on 2010-07-29
>  Ill need to find my config and commands to help you. I cant remember every thing any more 

Hm, ok. I guess I need the commands to create the xorg file first. Or would it be sufficient to c&p another one?

Thanks for the response btw ;-)

---

