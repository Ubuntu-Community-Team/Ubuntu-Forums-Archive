---
title: "What is the point of 'Labels' during the partitioning process?"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-11-22
Hello:

What is the point of 'Labels' during the partitioning process?

What are the benefits of 'Labels'?

What should I enter in 'Labels'?

Thanks,

---

### Post by matt_symes on 2010-11-22
Hi

Labels allow you to have a human readable name for a partition and help you identify each partition clearly. They are very useful on a system where you have multiple partitions.

Kind regards

---

### Post by Robert.Thompson on 2010-11-22
> **matt_symes said:**
> Hi

Labels allow you to have a human readable name for a partition and help you identify each partition clearly. They are very useful on a system where you have multiple partitions.

Kind regards

Thanks Matt.

---

### Post by srs5694 on 2010-11-22
To be 100% clear, the labels you enter when partitioning with most tools are probably *filesystem* labels, not *partition* labels. This may seem like a trivial distinction, but it's one that could come back to bite you if you misunderstand. This is because the Master Boot Record (MBR) partitioning system doesn't support labels, so on most disks there's only one thing that can hold a label (the filesystem contained in a partition) and being sloppy with terminology has no negative consequences. MBR is on its last legs, though, and its replacement is likely to be the GUID Partition Table (GPT) system. GPT *does* support partition labels, so when you switch to GPT (or if you're already using it, as for instance most Intel-based Mac users do), then there's the potential for confusion because the partition and the filesystem it contains can have different labels. Which label a tool presents is entirely dependent on the tool. For instance, IIRC GParted presents the filesystem label on GPT disks, but IIRC the text-mode GNU Parted (aka parted) and definitely the text-mode gdisk present the partition label. If you don't understand this distinction and know what your tools are doing, you could get very confused if you switch between tools that display different things.

---

### Post by Robert.Thompson on 2010-11-23
> **srs5694 said:**
> To be 100% clear, the labels you enter when partitioning with most tools are probably *filesystem* labels, not *partition* labels. This may seem like a trivial distinction, but it's one that could come back to bite you if you misunderstand. This is because the Master Boot Record (MBR) partitioning system doesn't support labels, so on most disks there's only one thing that can hold a label (the filesystem contained in a partition) and being sloppy with terminology has no negative consequences. MBR is on its last legs, though, and its replacement is likely to be the GUID Partition Table (GPT) system. GPT *does* support partition labels, so when you switch to GPT (or if you're already using it, as for instance most Intel-based Mac users do), then there's the potential for confusion because the partition and the filesystem it contains can have different labels. Which label a tool presents is entirely dependent on the tool. For instance, IIRC GParted presents the filesystem label on GPT disks, but IIRC the text-mode GNU Parted (aka parted) and definitely the text-mode gdisk present the partition label. If you don't understand this distinction and know what your tools are doing, you could get very confused if you switch between tools that display different things.

Thank you.

---

