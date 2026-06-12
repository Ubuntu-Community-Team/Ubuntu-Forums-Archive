---
title: "Upgrading to Ubuntu 10.04"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by GonchuB on 2010-04-20
I'm a begginer at ubuntu and I have never upgraded my os yet.
What I wanted to know is if my hard drive will be formatted when I upgrade from ubuntu 9.10 to ubuntu 10.04.

I have installed my ubuntu 9.10 recently and I don't wan't to have to backup my music and my files.

Does anybody know?

---

### Post by pbateman on 2010-04-20
Not if you upgrade instead of doing a clean install. I just upgraded a few weeks ago to the beta, all my files were left intact.

---

### Post by Paddy Landau on 2010-04-20
May I warn you to do a full backup anyway (I know you don't want to).

Not only is there a (small) chance of data loss on an upgrade, but there is anyway a chance of data loss when your hard disk finally stops working. And it will, one day, stop working!

Failing to have a backup is planning to lose your data.

---

### Post by KdotJ on 2010-04-20
> **Paddy Landau said:**
> Failing to have a backup is planning to lose your data.

+1
Been caught out twice now in the past. Now I ALWAYS back up my data.

Note to the OP, if you end up backing up your files, it might be worth doing a clean install to 10.04 anyway as it will be fresh and there are cases of systems not working properly after upgrades to the next version.

Just my opinion...

---

### Post by cespinal on 2010-04-20
> **KdotJ said:**
> +1
Been caught out twice now in the past. Now I ALWAYS back up my data.

Note to the OP, if you end up backing up your files, it might be worth doing a clean install to 10.04 anyway as it will be fresh and there are cases of systems not working properly after upgrades to the next version.

Just my opinion...

I know this topic is also recurring... I have not had good experiences doing online upgrades in the past, mostly because of $#&^! connections, but Im curious about how things have improved lately.

---

### Post by KdotJ on 2010-04-20
> **cespinal said:**
> I know this topic is also recurring... I have not had good experiences doing online upgrades in the past, mostly because of $#&^! connections, but Im curious about how things have improved lately.

I plan to do a clean install with 10.04, I just want it to be fresh and start from scratch with no potentially dodgy config files left over.
During the install I might even setup to create a separate /home partition...

---

### Post by AJH101 on 2010-04-20
Is there an option when installing to set a /home partition?!

---

### Post by Paddy Landau on 2010-04-20
> **AJH101 said:**
> Is there an option when installing to set a /home partition?
There was on prior versions. I haven't installed 10.04, but I would imagine that there is.

If I remember correctly, you need to do manual partitioning. Create three partitions:

[LIST]
[*]Swap (mount as 'swap')
[*]Root (mount as '/' or 'root', I forget which)
[*]Home (mount as '/home')
[/LIST]
They can be in any order.

---

### Post by PinchedNerve on 2010-04-20
Does anyone know if the 10.04 beta will be any different from the release candidate in 9 days?  I would hate to go with the beta & then have to reinstall again 9 days later.

---

### Post by Paddy Landau on 2010-04-20
I'm sure that there will be differences. I would wait.

---

### Post by cgul1 on 2010-04-20
> **PinchedNerve said:**
> Does anyone know if the 10.04 beta will be any different from the release candidate in 9 days?  I would hate to go with the beta & then have to reinstall again 9 days later.

My understanding is that you will be able to upgrade to RC and final from beta.
Beta has been working fine on my other laptop (main computer) I did a clean install of beta.
dont forget to backup any emails and the setup - dont ask why I now know this ....

cgul18-)

---

### Post by pbateman on 2010-04-20
I had a quick question, not to hijack the thread....if I currently have the beta installed and I run the updates every day, would that automatically upgrade me to the RC and eventually to the final release or do I have to manually install the actual RC and then the full version once they are available?

---

### Post by cgul1 on 2010-04-20
> **pbateman said:**
> I had a quick question, not to hijack the thread....if I currently have the beta installed and I run the updates every day, would that automatically upgrade me to the RC and eventually to the final release or do I have to manually reinstall the actual RC and then the full version?

again my understanding: update mgr shows an 'upgrade available' button at the top of the dialog when each becomes available.

cgul1 8-)

---

### Post by pbateman on 2010-04-20
Thanks! Just saw your post right after i had submitted mine.....

---

### Post by Phan76 on 2010-04-20
What;s the best way to do a back up before installing a new os as far as ubuntu is concerned ?

---

### Post by Paddy Landau on 2010-04-20
> **Phan76 said:**
> What;s the best way to do a back up before installing a new os as far as ubuntu is concerned ?
Two different types that I do.

[LIST=1]
[*]Back up your entire /home directory. That way, you can selectively restore anything that you need to restore.
[*]Back up your entire drive or, if you prefer, your partitions separately. That way if it's a total screw-up then you can restore to where you were. I use [CloneZilla]("http://clonezilla.org/") for this. Naturally, you'll need somewhere to store the backup; an external USB hard drive makes an excellent choice.
[/LIST]

---

