---
title: "Ubutnu software RAID 1 partitioning"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by tdapower on 2011-01-27
I need to configure ubuntu software raid 1 using 2 500Gb hard disks. Here are the partitions I need to create.
swap 8Gb
/ 50Gb
home 150Gb
data1 100Gb
data2 100Gb
data3 92Gb

But I was unable to create a boot location from these. So I created an additional partition of 2Gb. But When I do that I was unable to create more partitions.

I need to to know is ubuntu required Primary partitions for /, home,swap and boot. If any of these doesn't need Primary partitions, Then I can do my job

---

### Post by bioterror on 2011-01-27
[http://kuparinen.org/martti/comp/ubuntu/en/raid.html]("http://kuparinen.org/martti/comp/ubuntu/en/raid.html")

Any help from this one?

---

### Post by tdapower on 2011-01-27
Thanks for your reply, But I need to know about the partition types(primary/logical)

---

### Post by b0b138 on 2011-01-27
You can have 4 primary partitions. If you need more, then you can have 3 primanry, and 1 extended partition. In the extended, you can have many logical partitions.

---

