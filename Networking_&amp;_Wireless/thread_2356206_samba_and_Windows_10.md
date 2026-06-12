---
title: "samba and Windows 10"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by huffmanp on 2017-03-20
Why does Microsoft make things so difficult?

I was trying to re-establish some samba connections to my PC now that I have a Windows 10 machine.  I tried  the ubuntu 16 connect to a server dialogue in the Ubuntu File Explorer.  Couldn't get the authentication correct.  Went to terminal to try combinations with smbclient.  Who could of guessed what my user name is on the Windows 10 machine? It wasn't the name I use to log in.  It wasn't what is listed under Windows User Accounts, which is my full name, email address, and "Administrator".  It was the shortened version of my last name that I found as a folder under c:\users that contains my docs, pictures, etc. Why is that so hidden? 

However, once I discovered what my real user name was, I was able to mount some shares from Windows 10 to my ubuntu machine.

But what about Work Groups and browse lists?  My PC is in Work Group NELSON.LOCAL. My PC doesn't appear in Ubuntu's list under File explorer's Network tab. But if I continue to the Windows Network tab, I find the NELSON.LOCAL workgroup. If I try to open this workgroup, I get "Unable to access location. Failed to retrieve share list from server: Connection refused"  Am I supposed to get my Ubuntu machine into the NELSON.LOCAL workgroup somehow to get network browsing to my Windows 10 PC to work?  

Browsing the network from the Windows 10 PC shows my unbuntu machine's name and shares and allows a connection to the shares. But why isn't Windows network browsing symmetrical? Why does the network browse list on Windows seem to be different every day? How to I find my Windows Network browse list master and correct it?  Am I going to have to run a Windows domain for an office with just 10 people?

---

