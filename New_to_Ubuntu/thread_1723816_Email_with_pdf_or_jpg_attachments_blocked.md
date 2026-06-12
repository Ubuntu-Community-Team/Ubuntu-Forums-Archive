---
title: "Email with pdf or jpg attachments blocked"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by Wadcutter on 2011-04-07
I can't download POP3 email messages that contain either a pdf or jpg attachment. Such messages also back up the queue in my ISP's server so that no other messages that arrived after the one(s) with attachments can come thru. I can verify all of this by going the ISP webmail site. If, while there, I delete the attachments from the message, then it will come thru to my client(s) and the backed-up messages will also download.

I'm running Ubuntu 10.04 and using Opera 11.01 browser's built-in email client to download messages to view (but leave them on the POP3 server) and then I use Thunderbird 3.1.8 to also download and remove from the server so I can store select ones on my HD.

Up until about 10 days ago, everything was working fine. What changed, I don't know (other than regular Ubuntu updates).

Testing reveals that emails with Word and Excel attachemnts download fine and the attachments open in Open Office with no problem. But pdf and jpg attachments cause all email downloading to halt.

I have two HD's and run Win XP on the other drive (the original setup). I'm trying to migrate to Ubuntu as much as possible and hope to leave Win far behind one day. I have no problem with downloading the same messages in the Win version of Opera email client nor in Outlook. The issue apparently only affects Ubuntu (or Ubuntu versions of Opera and Thunderbird).

Any ideas? Am Ubuntu novice but intermediate Win user with almost 20 years of computer use behind me. Have been looking all over the forums and Google (actually Scroogle) for some hint of how to proceed. My ISP tech guy says the problem is not at his end and since it works in Win, I have to believe him.

---

### Post by chrisod on 2011-04-07
Do you have a firewall activated in Ubuntu that could be blocking the attachments?

---

### Post by Wadcutter on 2011-04-07
No, I checked gufw and a firewall is not activated. I originally had Clam installed, but uninstalled it after the email problems started, to be certain that it wasn't blocking anything. My usual line of thought from Windows experience is that if something won't download, it is either firewall or anti-virus issues.

Since my original post a couple of hours ago, I went to my email website to open the offending pdf attachment because I needed it for business purposes and it came up as a corrupted pdf file. So I rebooted into Windows and then it downloaded into Outlook and opened just fine. I'm now thinking my Ubuntu pdf reader program could be the issue. Maybe I'll re-install.

Thanks for your suggestion.

Before I waste anyone else's time. . . . . 
I re-thought the idea of a firewall being the culprit. Actually, ignorance is the culprit. I took a closer look and realized that there was also a firewall called Firestarter on my system. How it got there, I dunnno- the dog must have done it. Couldn't have been me.

So I uninstalled Firestarter and I uninstalled ufw/gufw and now the eamils and attachments that I couldn't download have changed their minds and are safely in my inbox and readable.

Because things were working fine a couple of weeks ago, and now they weren't, something must have activated one of these firewalls. My ISP went down for about 5 days just before the trouble started and that may have had something to do with it. I need to educate myself better about firewalls and intend to do so. (I'll skip the debate about their usefulness in Linux.)

Thanks again, chisod -you actually asked the right question but it took me a few to catch it.

---

