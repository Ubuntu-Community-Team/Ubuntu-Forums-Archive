---
title: "hp_wmi cannot hard-unblock wifi after coming back from sleep"
date: 2018-03-07
forum: Networking &amp; Wireless
---

### Post by manu-chroma on 2018-03-07
The wifi is hard blocked after coming back from sleep. 

I am particularly looking out for ways to disable the module responsible for flight mode key shortcut, so that it the wifi module doesn't get disabled on sleep. 

There has been a lot of discussion on this topic in the past and this issue plagues a lot of HP Pavilion laptops having rtl8723be module. 

This might be a helpful link in describing the problem: [https://bugzilla.kernel.org/show_bug.cgi?id=69131#c18](https://bugzilla.kernel.org/show_bug.cgi?id=69131#c18)

Any fixes are very much welcome and appreciated. Thank you!

---

### Post by praseodym on 2018-03-13
Lets try
```

sudo touch /etc/pm/config.d/00sleep_module               
sudo chmod +x /etc/pm/config.d/00sleep_module      
```
Now add

```
echo 'SUSPEND_MODULES="$SUSPEND_MODULES rtl8723be"' | sudo tee /etc/pm/config.d/00sleep_module
```
Check SUSPEND now

---

### Post by manu-chroma on 2018-03-18
Hi,

Thank you for your reply. Unfortunately, this doesn't work. The wifi is hardware disabled again after waking up from sleep.

---

### Post by manu-chroma on 2018-04-08
any help will be appreciated. I'm waiting patiently

---

