---
title: "how to connect to the wireless network builded by vista"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by wyattno26 on 2008-08-26
hello all,
I am new to this forum,and just get to ubuntu for a few days
here I get some problems:
my wired network doesnot work stablely .and,there isnot a wireless router in my apartment ,on the other hand,all of my classmates use windows, so,**I want to kown how to connect to the wireless network create by windows** ,:confused:
Thanks!
wyattno26

---

### Post by Blackcabs on 2008-08-26
Hi there,,, Not to sure exactly what you are asking ???. Are you trying to connect through one of your friends Pc's ,,or are you trying to connect to one of your friends network directly,,either way it doesn't matter whether its windows or not. 

Ps you are a braver person than me "asking questions about Windows" on this forum :evil:

---

### Post by wyattno26 on 2008-08-27
> **Blackcabs said:**
> Hi there,,, Not to sure exactly what you are asking ???. Are you trying to connect through one of your friends Pc's ,,or are you trying to connect to one of your friends network directly,,either way it doesn't matter whether its windows or not. 

Ps you are a braver person than me "asking questions about Windows" on this forum :evil:
Thanks for you reply!
I am sorry, maybe  I havenot presented my question  clearly:
I want to share the network of my firend though wifi and his OS is vista . I tried "iwconfig wlano essid '***'",but the signal is
always 0%
ps I do think it is a question about ubuntu  not windows

---

### Post by Blackcabs on 2008-08-27
> **wyattno26 said:**
> Thanks for you reply!
I am sorry, maybe  I havenot presented my question  clearly:
I want to share the network of my firend though wifi and his OS is vista . I tried "iwconfig wlano essid '***'",but the signal is
always 0%
ps I do think it is a question about ubuntu  not windows

Sorry wyattno26 that i didn't answer sooner.Let me get this right... So you are trying to access folders on your friends Vista machine via a wifi link or are you trying to access the internet DIRECTLY using his connection.If you are trying to get on the net then it doesn't matter that he has vista. Can you tell me if you always configure your wifi connections manually or do you use Networkmanager to do this.

---

### Post by wyattno26 on 2008-08-29
> **Blackcabs said:**
> Sorry wyattno26 that i didn't answer sooner.Let me get this right... So you are trying to access folders on your friends Vista machine via a wifi link or are you trying to access the internet DIRECTLY using his connection.If you are trying to get on the net then it doesn't matter that he has vista. Can you tell me if you always configure your wifi connections manually or do you use Networkmanager to do this.

I have never configure my wifi connections manually as I think it is working naturally. I tired to access to the  internet directly  useing my roommate's connection because my wired network is not stable enough ,but the signal is always 0% while i can find the network he create.
ps :Thanks for your reply in spite of my awful English !

---

### Post by Blackcabs on 2008-08-29
> **wyattno26 said:**
> I have never configure my wifi connections manually as I think it is working naturally. I tired to access to the  internet directly  useing my roommate's connection because my wired network is not stable enough ,but the signal is always 0% while i can find the network he create.
ps :Thanks for your reply in spite of my awful English !

Ok so you are using network manager to run your connections,What do you mean you find the "network he create".. your wifi card must be working or you would not see anything. Make sure your room mates wifi Router is set
 to broadcast its ESSID . Can you click on the network icon that shows what networks are available,,and see your room mates connection

---

### Post by itsjareds on 2008-08-29
Does your friend know you are doing this? If not, he might have a password on his internet connection preventing you from connecting.

---

### Post by wyattno26 on 2008-09-03
> **Blackcabs said:**
> Ok so you are using network manager to run your connections,What do you mean you find the "network he create".. your wifi card must be working or you would not see anything. Make sure your room mates wifi Router is set
 to broadcast its ESSID . Can you click on the network icon that shows what networks are available,,and see your room mates connection

of course, I have gor the correct ESSID and password,but,I still cannot connect to his PC,I was wondering whether there is something wrong with my samba setting,if so,I hope someone can told me the details......

---

### Post by Blackcabs on 2008-09-03
> **wyattno26 said:**
> of course, I have gor the correct ESSID and password,but,I still cannot connect to his PC,I was wondering whether there is something wrong with my samba setting,if so,I hope someone can told me the details......

So you are trying to connect through your friends PC ""AD-HOC"" I think that with samba you can only share his files you cannot connect to the net..You would probably have to use SSH with a tunnel.

---

