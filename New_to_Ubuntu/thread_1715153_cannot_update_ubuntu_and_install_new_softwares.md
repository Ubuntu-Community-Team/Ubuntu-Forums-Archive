---
title: "cannot update ubuntu and install new softwares"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by jaj540 on 2011-03-26
I am a absolute beginner in Linux.I cant update my ubuntu.. an error comes such as 
"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."

I have recently cleaned packages and purged PPAs using Ubuntu tweak...
Is it because that... some told i lost some keys..what is that? how will i fix this problem..?pls help me

---

### Post by mörgæs on 2011-03-26
What happens if you boot the machine and run the commands

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by 5149.5 on 2011-03-26
> **jaj540 said:**
> The action would require the installation of packages from not authenticated sources."

I have recently cleaned packages and purged PPAs using Ubuntu tweak...
Is it because that... some told i lost some keys..what is that? how will i fix this problem..?pls help me

This is due to the ubuntu keyserver being offline which prevents you from authenticating the source of the software. 

I'm not sure what is going on. There are several keyservers that are offline.

---

### Post by aaaaalex on 2011-03-26
I haven encoutered that issue in the past. Here is what fixed it. 

In the Update Manager, click on 'Settings' at the bottom left hand corner of the window. 

Then on the first tab of the Software Sources Window 'Ubuntu Software' click on the drop down menu 'Download from' and select 'Other...'.

In the new window Choose Download Server click on 'Select Best Server' towards the top right of the window. 

Wait a few moments as the best server is being determined and finalize it by clicking on 'Select Server'. 

I am not entirely sure how that related to the previous post but it always did the trick for me. 

Btw. I have only encountered that phenomenon recently, i.e. in the time of Maverick.

---

### Post by jaj540 on 2011-03-27
@aaalex....
thanx ..changing the server resolved the problemm....
thanx guys for helping me out:P

---

### Post by opsc05 on 2011-10-22
> **aaaaalex said:**
> I haven encoutered that issue in the past. Here is what fixed it. 


Then on the first tab of the Software Sources Window 'Ubuntu Software' click on the drop down menu 'Download from' and select 'Other...'.

In the new window Choose Download Server click on 'Select Best Server' towards the top right of the window. 

Wait a few moments as the best server is being determined and finalize it by clicking on 'Select Server'. 

I am not entirely sure how that related to the previous post but it always did the trick for me. 


In the Update Manager, click on 'Settings' at the bottom left hand corner of the window. 


Btw. I have only encountered that phenomenon recently, i.e. in the time of Maverick.

Thank you for your complete answer. I do not know if my upgrade will be successful but at least it seems to be running now.

After Win7 crash I decided I'm through handing over money to every pc  for software that should have been sent with the machine. I am on day  two of Ubuntu. While it is a bit daunting I am hoping to learn it by New  Years :D
 If only I could shutdown all the password requests. Thank you for taking the time to help others.

---

