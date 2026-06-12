---
title: "vmbuilder postfix configutation error?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by shain on 2009-06-18
I'm working on setting up a virtual server on my machine to run a backend cmp on for website management.  

I tried to install vmbuilder by typing this command:

```
 sudo apt-get install python-vm-builder 
```It looks like I getting stuck, but this could just be me not knowing anything about using terminal.  After what looks like a successful install I get to a screen that says:


    Please select the mail server configuration type that best meets your   &#8593; 
  &#9474; needs.                                                                  
  &#9474;                                                                         
  &#9474;  No configuration:                                                      
  &#9474;   Should be chosen to leave the current configuration unchanged.        
  &#9474;  Internet site:                                                         
  &#9474;   Mail is sent and received directly using SMTP.                        
  &#9474;  Internet with smarthost:                                                
  &#9474;   Mail is received directly using SMTP or by running a utility such     
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                
  &#9474;  Satellite system:                                                      
  &#9474;   All mail is sent to another machine, called a 'smarthost', for        
  &#9474; delivery.                                                               
  &#9474;  Local only:                         
      No configuration:                                                      
  &#9474;   Should be chosen to leave the current configuration unchanged.        
  &#9474;  Internet site:                                                         
  &#9474;   Mail is sent and received directly using SMTP.                        
  &#9474;  Internet with smarthost:                                               
  &#9474;   Mail is received directly using SMTP or by running a utility such     
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                
  &#9474;  Satellite system:                                                      
  &#9474;   All mail is sent to another machine, called a 'smarthost', for        
  &#9474; delivery.                                                              
  &#9474;  Local only:                                                            
  &#9474;   The only delivered mail is the mail for local users. There is no      
  &#9474; network.                                                                
  &#9474;                                                                           
  &#9474;                                 <Ok> 

Nothing is clickable, obviously, and there is no cursor to input. It appears to me like it wants some kind of input before it goes on, but I dont know how to oblige it.  

Thanks.

---

### Post by Villiam on 2009-06-18
Have you checked this official documentation on vmbuilder over here: [https://help.ubuntu.com/8.04/serverguide/C/ubuntu-vm-builder.html](https://help.ubuntu.com/8.04/serverguide/C/ubuntu-vm-builder.html)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by shain on 2009-06-18
yes I have.  I am not sure that that site addresses my issue at all. If it does, then I am not seeing it, but I went ahead and went by their instructions.  Their first instruction was to type in:

```
**sudo ubuntu-vm-builder kvm hardy --addpkg vim** 
```I just get 

sudo: ubuntu-vm-builder: command not found

---

### Post by shain on 2009-06-19
Still having trouble with this.  Any ideas?

---

### Post by walter554 on 2009-06-29
shain, I'm struggling with kvm myself - hence I found your post. However, I've installed ubuntu-vm-builder ok.
1) Maybe ubuntu-vm-builder isn't working for you because you installed python-vm-builder. Try 
```
 
apt-get install ubuntu-vm-builder

```
You'll still get the postfix screen, but maybe you can chose some options with the keyboard. 
 
Why a mail system (and maybe a dns) is being installed as part of a VM builder is not entirely clear to me - either a huge assumption by someone or KVM is really wierd. I'm close to reverting to VMWARE which at least installs and runs out of the box.

---

