---
title: "How to check if SSL is working?"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by TrialVersion on 2010-11-08
p { margin-bottom: 0.21cm; }  Hello.

Platform: ubuntu 10.4 + Firefox 

I have some doubts about https websites and checking the security I have found some strange stuff and I'm not sure of what it means.

I tried to convert http web site and add a 's' so it reads "https"
then said web site changed to https successfully :confused:
I even checked the certificate an it was correct....Firefox said that it was encrypted with RC4 128 bit.

After that checked other websites and found 3 main groups of websites:

i  .- If you add the 's' it becomes https. Ex: google main page
ii .- If you add the 's' it returns to http. Ex: slashdot main page
iii.- If you add the 's' it does not connect. Ex: tom's hardware

Is firefox wrong when it tells you that a web page from the first group is encrypted? 
How could I be sure that a https website is actually encrypted and did not just add the “https” to the url to deceive me?
 

 Thank You.

---

### Post by geoffmcc on 2010-11-08
To have a "secure" connections with https it has to be setup on the server end.

Like you have found- some sites like google will support it, others will just refer you back to http and then the rest just wont display a page.

In order to accept ssl connections to their site they have to enable it. I believe you said you were running a site - you probably enabled default-ssl under /etc/apache2/site-available and therefor your site accepts secure connections.

But please... Don't think that ssl is secure. I have been doing some testing on my home network with sslstrip and it is disgusting that i can man in the middle and get passwords if anyone on my network logs into facebook or some other site (bank sites and what not)

SSL needs to be fixed!!!

---

### Post by TrialVersion on 2010-11-08
So if the server is suporting it , it is actually encrypted as Firefox shows in the certificate? 
It is not a Firefox bug? 

Well , even if SSL is not 100% secure it is better than http.

It was mostly because I found a online shop that has that problem.
It connects by default as http and I didnt like that. So I tried adding the 's'...
You have to add the 's' "by hand" to connect to it as secure.:mad:

So after that i wondered if that "hand made https" works and if other 
secure websites I used are not secure because they could be disguised by adding "https" in the links.

Thanks You.

---

### Post by TrialVersion on 2010-11-09
Sorry;
Could someone confirm that the encryption is working when the 'http' is changed to 'https' manually , please.

Thank You.

---

### Post by toekneewood on 2010-11-10
If your URL has https in it then your connection to the Server is secure.  Your get 2 type of certificate.  Ones that you purchase and install on your web server so that the user does not get prompted.  And ones that you can self sign and put on your Server that you create from your own CA Server.  The self sign ones will prompt for confirmation when the user connects to your https.

Hope this helps a little

---

