---
title: "dell studio 15, brightness issue"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Falc7 on 2009-07-06
Hi
I have a dell studio 15, and my brightness keys don't work, which is a shame as the screen is unconfortably bright atm. I saw the solution posted below, but i don't have a /usr/src/linux folder, just some folders which relate to which kernal i am using, obviously i should choose the newest one, but should i edit the 'generic' folder or the one which isen't generic?

Also, as i am editing a kernal file, does this mean that i will have to do this modification every time i get a kernal update?

> **shiBBy2k7 said:**
> Even registered to write that message ;)

According to the Brightness-Key issue: I found a little & dirty but working workaround for that issue but you have to recompile your kernel.


Go to your kernel sources, usually /usr/src/linux/drivers/acpi
Then edit "ec.c" and comment the following line out:
```
static int acpi_ec_transaction(struct acpi_ec *ec, struct transaction *t,
                               int force_poll)                           
{                                                                        
        int status;                                                      
        u32 glk;                                                         
        if (!ec || (!t) || (t->wlen && !t->wdata) || (t->rlen && !t->rdata))
                return -EINVAL;                                             
        if (t->rdata)                                                       
                memset(t->rdata, 0, t->rlen);                               
        mutex_lock(&ec->lock);                                              
        if (ec->global_lock) {                                              
                status = acpi_acquire_global_lock(ACPI_EC_UDELAY_GLK, &glk);
                if (ACPI_FAILURE(status)) {                                 
                        status = -ENODEV;                                   
                        goto unlock;                                        
                }                                                           
        }                                                                   
        if (ec_wait_ibf0(ec)) {                                             
                pr_err(PREFIX "input buffer is not empty, "                 
                                "aborting transaction--\n");                
                status = -ETIME;                                            
                **//goto end; **                                                

        }
        status = acpi_ec_transaction_unlocked(ec, t, force_poll);
end:                                                             
        if (ec->global_lock)                                     
                acpi_release_global_lock(glk);                   
unlock:                                                          
        mutex_unlock(&ec->lock);                                 
        return status;                                           
}
```then go to /usr/src/linux and do the following commands:

```

make oldconfig
make prepare
make

```Go away and wait ;)

After finishing (without errors) you can copy your new kernel with:
```
cp /usr/src/linux/arch/x86/boot/bzImage /boot/vmlinuz-*YOURKERNELVERSION*
cp /usr/src/linux/System.map /boot/System.map-*YOURKERNELVERSION*
mkinitrd
```As I applied my patch the EC error message still appears but brigthness can still be controlled. Also detection whether ac is plugged or not works perfectly.

Hope this helps
Regards
shiBBy2k7

PS: It would be nice, if you could give some feedback ;)
My bugreport @ Novell: [https://bugzilla.novell.com/show_bug.cgi?id=517173](https://bugzilla.novell.com/show_bug.cgi?id=517173)

---

### Post by Falc7 on 2009-07-09
bump, anyone know how to get my brightness controls working, or edit that file so i can try it myself? I can't even see an ec.c file

---

### Post by superprash2003 on 2009-07-09
which keys do you use to increase/decrease brightness?

---

### Post by Falc7 on 2009-07-11
i tried using the panel object for brightness, and also the keyboard keys

---

### Post by superprash2003 on 2009-07-11
do you mean using the Fn button? I think its Fn+F5 or F6 right?

---

### Post by Falc7 on 2009-07-12
Its fn and F4 and F5 :)

---

### Post by Falc7 on 2009-08-02
Can anyone help me? Its really far too bright normally. The keys work under windows

---

### Post by thychamp on 2010-04-20
Has anyone been able to solve this issue.  I have a dell studio 15, just installed Ubuntu 10.04 beta 2 64-bit and I am having the same problem.  I cannot dim the screen using F4 and F5.ubuntu forums

---

### Post by Bill Gnates on 2010-05-12
I have a Dell 1110 netbook and I've had this problem since I originally installed Ubuntu on it about 6 months ago. Please help!

---

### Post by thychamp on 2010-05-13
The bigger issue I ended up having with my Dell Studio 15 was the function keys would lock up my keyboard and mouse when using them.  I would then have to resort to doing a hard reboot of the laptop.

I also discovered that I could not hibernate or put the laptop to sleep.  I use these functions everyday and found it difficult to have to deal with it not working.

I spent quite a few hours trying to resolve these issues.  Since I was not able to I had to reinstall Windows 7 on my machine.

I have had much better luck with my previous laptops running Ubuntu.  It would be nice if more hardware vendors worked with Ubuntu to ensure the consumer that there hardware works with Ubuntu.

---

### Post by edwardLS on 2010-05-13
I have a Dell Studio 1555 with Lucid Lynx installed, and my Brightness keys on the keyboard work.

Are you using Lucid Lynx?  I had trouble with brightness on Karmic Koala on the same Dell Studio 1555.

---

### Post by thychamp on 2010-05-13
> **edwardLS said:**
> I have a Dell Studio 1555 with Lucid Lynx installed, and my Brightness keys on the keyboard work.

Are you using Lucid Lynx?  I had trouble with brightness on Karmic Koala on the same Dell Studio 1555.
I was using Ubuntu 10.04 Beta 2 64-bit.  I have a Dell Studio 1558.  Are you using the 32-bit or 64-bit version of Ubuntu?

---

### Post by edwardLS on 2010-05-13
I am using the 64-bit released version of Lucid Lynx.

---

