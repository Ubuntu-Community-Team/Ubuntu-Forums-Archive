---
title: "Accessing Windows Shares in a Domain"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by BattleGnome on 2008-06-27
I am wondering how I can access Windows Shares on the Domain. When logging into ubuntu I am not using a domain login, nor is the machine connected to the domain. 

If I select Places > Network I can see the Windows Network, digging deeper I can see our domain, and under that I can see all our machines. If I double click on a machine which I know has Windows Shares nothing appears?

---

### Post by superprash2003 on 2008-06-27
go to the terminal and type sudo nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine which you want to access files from

---

### Post by Kileli on 2008-07-11
> **BattleGnome said:**
> I am wondering how I can access Windows Shares on the Domain. When logging into ubuntu I am not using a domain login, nor is the machine connected to the domain. 

If I select Places > Network I can see the Windows Network, digging deeper I can see our domain, and under that I can see all our machines. If I double click on a machine which I know has Windows Shares nothing appears?

This is the exact same issue i am having. i have 3 workgroups and one domain. When i access the computers on the workgroups i am able to see the shares just fine.

I have joined the domain successfully via likewise. how do i authenticate my session. i need to log into the domain with my windows credentials
is that even possible?

---

### Post by anon0 on 2009-04-08
> **BattleGnome said:**
> I am wondering how I can access Windows Shares on the Domain. When logging into ubuntu I am not using a domain login, nor is the machine connected to the domain. 

If I select Places > Network I can see the Windows Network, digging deeper I can see our domain, and under that I can see all our machines. If I double click on a machine which I know has Windows Shares nothing appears?

I have the same problem now. If I do "sudo nautilus smb://x.x.x.x" I get an error message "nautilus cannot handle "smb" locations"

Any more ideas?

---

