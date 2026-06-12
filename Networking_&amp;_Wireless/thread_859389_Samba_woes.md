---
title: "Samba woes"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by catonano on 2008-07-14
Hello people,

well I have a public shared folder with samba, a bunch of Vista based clients and one Ubunutu hardy client.

My desktop users use gmail A LOT. Sometimes they attach files from the shared folder to their emails.

The gmail web page for composing a mail message has a field with a button aside. You press the button and a "open file" dialog windows pops up; you select the file and the path appears written in the field. This is how it should go.

It goes like that, actually, but for the Vista based clients ONLY.

The Ubuntu based client ends up with NO PATH in the field.

I tried to share that folder via nfs and mount it vie nfs and IT WORKED

So I guess there must be a difference between the Vista samba client layer and the Ubuntu samba client.

Well, the nfs trick works ONLY if the client user is in the root group on the client machine, otherwise it does NOT.

Further, I'd love to avoid having two distinct sw layers for doing the same thing, that is share a folder.

So, I'd love samba to work, if that's not going to be the case, I'd love if nfs would work.

Actaully, I'd be grateful to get some help on any side of the matter ;-)

Thanks a lot
Bye
Cato

---

