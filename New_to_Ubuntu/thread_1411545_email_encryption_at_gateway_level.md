---
title: "email encryption at gateway level"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by neha srinivas on 2010-02-20
hi.. i m working on a school project to develop a gateway to encrypt emails. i ve no idea as to how to start pl help. i searched the net a lot but found only existing products which are available.. pl guide me as in what direction to proceed. 

and if i use any of the gateways will i be able to incorporate my own email encryption algorithm into it???

by the way i use ubuntu 9.04 if it makes any difference....

---

### Post by HermanAB on 2010-02-20
Howdy,

First you need to do a threat risk analysis.  In other words, define what is the perceived problem that you want to protect against.  You also need to look at what is technically feasible from an interoperability point of view.  For example:
1. Encrypt the mail store on the server: Prorotects against administrators reading the mail on the server and against a server getting stolen resulting in data disclosure.
2. Encrypt link between servers: Protects against snooping on a world wide level.  Only works if the destination/source mail server is also encrypting.
3. Encrypt link between server and mail clients: Protects against snooping on the LAN - wired and wirelessly.

Once you have decided what you want to do and why, then look around for a solution again.

---

### Post by neha srinivas on 2010-02-20
i ve done the initial analysis i want to encrypt my emails between servers

---

### Post by neha srinivas on 2010-02-20
i will be testing it on my machine so i ve already set up a virtual machine on my system.

i wanted to set up a mail server on each of them which will pass the emails to another server/gateway for encryption/decryption...

by the way thanks for the reply and thanks for all the future help:o really appreciate it

---

### Post by HermanAB on 2010-02-20
Howdy,

If you want to encrypt email between servers on a corporate WAN over the internet, then all you need is SSMTP on port 465.  That is, SMTP over SSL.  You can do that with Stunnel.

The problem is that you still need to allow email to/from insecure outside systems over port 25.

Hope that helps.

---

### Post by neha srinivas on 2010-02-20
is this not like one of the many solution available????

my project should have my own encryption technique like say RSA or AES involved in it.

is that possible????

---

### Post by ja660k on 2010-02-20
what language are you planning to write this in?
it sounds like you are trying to create your own protocol

---

### Post by m.brinkers on 2010-02-20
Take a look at Djigzo ([www.djigzo.com](www.djigzo.com)). Djigzo email encryption gateway is an email server that automatically encrypts and decrypts your incoming and outgoing email. Djigzo is compatible with any existing email infrastructure. Djigzo supports two encryption standards: S/MIME and PDF encryption. Email that is encrypted and digitally signed by Djigzo can be read in Outlook, Thunderbird and other mail clients. PDF encryption allows secure, encrypted email delivery without requiring any client encryption software.

Djigzo is free and open source and can be downloaded from [www.djigzo.com](www.djigzo.com). Djigzo can be installed using any of the provided packages for Ubuntu Linux, Red Hat and CentOS. A ready to run "Virtual Appliance" for VMware ESX and Workstation is available as well. It's written in Java and can be extended with your own encryption.

---

### Post by neha srinivas on 2010-02-20
i m planning to write it in java..

---

### Post by neha srinivas on 2010-02-20
i have actually gone through Djigzo.....

it provides its own encryption facility right.. but i actually need to incorporate my own encryption method using one of the encryption algorithms..

anyway i can include that in digizmo??? or any other way to proceed???

---

### Post by neha srinivas on 2010-02-20
ok thank u so much for the help... i shall ask for further help about including my encryption technique into it...

thank u so much really appreciate it....

---

### Post by ja660k on 2010-02-20
i dont think there is an easy way to do this
its easy to write an email client that sends encrypted mail that connects through port 25 but the problem here is receiving, the mail server wont decrypt it...

so if you write your own email client then sends the encrypted mail,and decrypts received mail.
you can still use the SMTP protocol already in place

---

