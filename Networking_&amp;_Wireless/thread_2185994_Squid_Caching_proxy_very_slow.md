---
title: "Squid Caching proxy very slow"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by DieEier on 2013-11-05
Hi all.

I am setting up a second squid caching proxy to run behind my current squid proxy. The reason for this is that I cannot mess around too much with our current proxy, but I need a small part of our network to be controlled by the second proxy to allow for dhcp and user name based auth. 

I have set up squish on the second proxy running Ubuntu 12.04 lts. Everything seems ok, but when I start the proxy my client gets maybe a minute of fast browsing, then the page load times start stretching into minutes. When 'n stop squid and reload the page it works for a minute or so and then becomes slow again.

My 1st proxy runs squid 2.7 on slackware 12.1. It is set up as a transparent proxy with ip based acl's.
My 2nd proxy runs squid 3.1 and uses squish for username based filtering.

Has anyone else run 2 squid servers in series and had the same problem? I really want to deploy this server to provide our boarding kids internet access while still keeping their usage in check, but currently the internet acces through it is slow with even one client.

Can any one help me or make any suggestions?
:P

---

### Post by SeijiSensei on 2013-11-05
This might help, though I've not done anything like this myself:  [http://wiki.squid-cache.org/Features/CacheHierarchy](http://wiki.squid-cache.org/Features/CacheHierarchy)

---

### Post by DieEier on 2013-11-06
Thanks, I'll check it out

---

### Post by DieEier on 2013-11-06
Thanks [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")
This seems to work, but it also seems to break squish. Squish no longer seems to pick up the traffic from users, which is essential for my user based quota system.
After some digging I did find that putting an allow acl for my second proxy at the very top of the proxy restrictions in the main proxy solved the slow browsing without setting up cache peering.
I suspect this is not ideal, so I will keep digging and report back.
Thanks for the help so far.

---

### Post by DieEier on 2013-11-12
Hi everyone

After struggling and searching for several day I  finally got it right. It seems that setting the parent proxy also did  not work. I installed a different HDD and tried the IPCop distro. I can  highly recommend this since it works almost straight out of the box,  including user based auth using basic, ntlm , raduis, ad etc. 

The only problem was that I could not set automatic user quotas. Apparently this will be available in v2.1 .

Until  then I needed to make my firewall work, so I decided to start from  scratch with ubuntu server 12.04 lts and squid. After getting squid  going with only an allow all acl, I found that it was reasonably fast  (not brilliant, since the hardware running the server is 10 years old).
After  I installed squish things slowed down a little, but it is still  reasonable. My guess is that with all the different monitoring tools  that I tried and removed that I missed a script or something somewhere.

Here is what I learned for anyone who may need to do this in future:
1. It's ok to try everything until you know what you really need, but then it is good to start clean with a clear roadmap.
2.  Try IpCop, Sphirewall etc. sometimes it can be enlightening to see how  others approach a proble, or their solution may even just work for you.
3.  Squish is a wonderful but very dated solution which will still work  with apache2 and squid 3. There is a catch. When you get the install  package, make a copy and get your hands dirty. All the file system  references for squid need to change to squid3 ie /etc/squid/squid.conf  becomes /etc/squid3/squid.conf. This is because when squish was created  squid still resided in the old dirs. Same applies to apache2. If you are  unsure about where the files are that get referred in the different  scripts then find the by doing the following on your server cli.
   3.1 Update the database of files using command "sudo updatedb"
   3.2 When this command finishes (could take a minute) find the filename using "sudo locate 'filename" ie "sudo locate squid.conf"
I will try to make this easier by posting an updated install zip when I get the opportunity.

4. When editing any config file MAKE A BACKUP before hand. Use "cp 'filename' 'filename.bak'". If you mess up just do the reverse to restore the file.
5. When editing a config for a service (like squid) then stop the service. Start editing the file, write (save ) the file, but keep the editor opn. Start the service. If an error occurs then you know exactly where things went wrong and you can correct them immediately. This helps troubleshooting. Also commenting out lines help to narrow down problem areas.

6. Ask for help. Forums are full of wonderful people who want to help. 
7. When you succeed then go back to your post and tell everyone how you did it so that they know how to solve the problem too.
8. Say thank you. Enough said.

Thanks to everyone on the forums who help people like me every day.
I hope this post helps someone else in future. Good luck!

:guitar:

---

