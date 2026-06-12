---
title: "Ubuntu 8.10 + Webmin + Godaddy Problem"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by mrmikey05 on 2009-03-22
Hey everyone. I am a newbie(NOOB). I have completely installed Ubuntu 8.10 Server Edition and Webmin as the Control Panel. I registar myself a domain name at Godaddy.com(choose to host my own server). 

My Question is how am I suppose to use my domain name to enter my website? Everytime I look around on google and here, DNS, A Record, and Name Server appear. But like I said, I am a noob, and do not understand any of these. 

I found some tutorial on google and did what it says. Can't remember the site names but remember one is from here. Well, this is what I did so far:

I went to Godaddy.com and click on Domain Manager. Click on Total DNS Control and MX Records. Inside, it have A (Host), CNAMES, NAMESERVER that are configured. So I add a New "A Record" with:
Host = my domain name (example.com)
Point to = 192.168.1.66 (my static ip address for my ubuntu server)
Time to Live = Default

Create DNS BIND in Webmin. 
Server > DNS BIND Server > Create Master Zone.
Fill out form as follow: (example.com isn't my real domain name)
Zone type = forward (name to address)
Domain name = example.com
Record File = /var/www/example
Email address = [email]webmaste@example.com[/email]
Use Zone Template = No
IP address for Template record = 192.168.1.66
> Save

I then go to Apache Server and create virtual host with the following configuration:
Handle connection to address = Specify: 192.168.1.66
Port = 80
Document Root = /var/www/example
Server Name = example.com
Add virtual server to file = standard httpd.conf file
Copy directive from = nowhere
> Create

I then test if my domain is working or not? It is not working. Waited til the next day and still don't work. Now I am stuck. Please help me because I am frustrated. I just need to find out how to use my domain name that I just registar from Godaddy.com. Sorry if everything is wrong or confusing. 

If you prefer a different Control Panel, teach me how to uninstall this one first because I can't find anywhere on how to uninstall this Control Panel. Also tire of reinstalling ubuntu to start off fresh again. Did that 3 time already. This server is still fresh with no webpage or anything except the control panel.

Thanks in Advance,
Mikey X.

---

### Post by jasonsjunk on 2009-03-22
The problem is you are using your LAN IP not your WAN IP.  I too self host a sever from my house using a similar setup (Webmin, Go Daddy etc.)  

Here is what you need to do.  
1) Go to [http://www.whatismyip.com/](http://www.whatismyip.com/) to find out your external IP address.  
2) Change your A record to the address you found in step 1.
3) While your logged into your GoDaddy acct you should also create a CNAME so [http://www.yourdomainname.com](http://www.yourdomainname.com) points to [http://yourdomainname.com](http://yourdomainname.com)  
4) Go into your router config and make sure port 80 is forwarded to the internal ip address of 192.168.1.66 
5) Disable BIND there is no need for you to run a DNS server since Go Daddy is handling DNS for you.  Running a DNS server is a pain in the *** and you should only run one if you know how to and need to.  
6) As for Apache you can specify localhost and your external ip address for the handle connection to address directive.  

Also are you sure you have a static ip address from your ISP?  I do but I had to pay extra.  If you aren't sure your external IP is static you will need something like Dynamic DNS from [www.dyndns.com](www.dyndns.com) to keep track of your IP address.  If you go that route you will have dyndns handle all of the DNS stuff and GoDaddy will just be your registrar.

---

### Post by mrmikey05 on 2009-03-22
Um. I am not sure if command: nano /etc/network/interfaces lead to making it static for sure. I set it up as static according to Ubuntu Geek tutorial. But if it not then, I will use dyndns.com.

How do I find my server external IP if I am SSHing into it only? I don't have a desktop install. Just Server Edition with Webmin.

And another thing, do I have to undo everything I already made in GoDaddy? 

Thanks for a quick response,
Mikey X.

---

### Post by aago1254 on 2009-07-07
i dont want to loose my emails that i pay for that is hosted thru go daddy i want to serve both my emails and website myself.  i have no idea how to keep go daddys dns server but have there dns point to my wan ip and if so how to change my wan ip when the ip changes i have comcast and they dont really like websites on a resident account. and i notice the ip doesnt change often.  so me paying for a ip wouldnt make sense if it doesnt change much.. any way that my problem  > where do i go in godaddy to change where the dns points and after that i can figure the server out by scratching my head and looking at forums .

---

