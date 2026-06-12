---
title: "(Regularly) Sync one imap email account to a gmail account with Thunderbird"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by hanzj on 2010-09-18
1. Description of the Situation
So I have one email account(let's call it Account ABC) that I could access via IMAP. I have been using Thunderbird to access Account ABC. Now, what I would like to do is to have all the emails on Account ABC "copied"/synced into another account, specifically, a brand-new gmail account. It has to be gmail because I love its powerful search and features. Account ABC does _not_ have POP access. Gmail cannot access another account via IMAP. So I think we must use a middle-man solution for this problem. Can Thunderbird or some other middleman service/software, help with this problem? 

I don't expect the copying/syncing to be automatic. But I also don't want to have to do the equivalent of forwarding each message one at a time from Account ABC to the gmail account.

---

### Post by Paddy Landau on 2010-09-19
Most webmail providers provide an auto-forward facility. Does your ABC account have such a thing? You could auto-forward to your Gmail account.

Then your Thunderbird can download directly from the Gmail account.

Strange that it doesn't have POP access, though -- most unusual!

If that solution doesn't work for you (if ABC doesn't have an auto-forward feature), then you could use a message filter in Thunderbird.

[LIST]
[*]Tools > Message filters
[*]Filters for: ABC
[*]New
[*]Match all messages
[*]Forward message to: Gmail account
[*]+ Delete message
[/LIST]

---

