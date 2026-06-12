---
title: "How to set up wifi link as AP in ubuntu?"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by kirbyboy on 2008-07-07
Hi, i have tried to set up my wifi link(is to connect a PSP or a DS to internet throught a PC) as an access point(master mode) in ubuntu, but the only i get is:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
Can somebody help?
Usually, the ZD1211 driver should be compiled, but it's imposible because the linux/config.h doesn't exist anymore, so i use the ZD1211rw driver which is installed by default in the kernel, so i don't know which is the problem.
If you want to know, this is the wifi link:
[http://www.mayflash.com/pc/pc041/pc041.htm](http://www.mayflash.com/pc/pc041/pc041.htm)
but the web page doesn't offer much help with linux, only windows, where it works, so i known it's posible to make it an access point.
Thanks in advance.

---

### Post by guedesav on 2008-10-25
I've got one of those, too. Actually, there is a manual for Linux along with the driver in the CD(if it came in the CD, that is...). But you might as well as ignore it, it won't work.

First of all, get rid of the zd1211rw driver and compile the zd1211b available at sourceforge.

Then I suggest you try this topic: [http://ubuntuforums.org/showthread.php?t=422499](http://ubuntuforums.org/showthread.php?t=422499) (It has a link for the sourceforge page as well). It was the one that got closer to a solution. I'm trying to contact the author for some help, if I manage to configure the thingy to work, I'll let you know.

---

### Post by kirbyboy on 2008-10-27
Thanks, i'll try it later in my home.

---

### Post by kirbyboy on 2008-10-27
No luck, the problem is that the drivers can't compile with actual kernel, i think.  If only the driver could compile...

---

### Post by guedesav on 2008-10-27
I had no problem compiling the vendor based driver(it supports Master Mode, even). Here's the link: [http://zd1211.wiki.sourceforge.net/VendorBasedDriver](http://zd1211.wiki.sourceforge.net/VendorBasedDriver)

Try again with this one if you manage to compile it.

---

### Post by kirbyboy on 2008-10-28
Hi, i tried that yesterday, this is the first error i get:
‘struct sk_buff’ no tiene un miembro llamado ‘mac’ => in english it would be something like "‘struct sk_buff’ doesn't have a member named ‘mac’"

I get more errors, which kernel are you using?, mine is 2.6.24-19-generic

I think i have all the needed packages.

---

### Post by guedesav on 2008-10-28
My kernel is 2.6.20-17-generic. I had no problem compiling it whatsoever.

Check the file /usr/src/your-kernel-source/include/linux/skbuff.h for a struct sk_buff.

Also, do you have your kernel source? Just to check...

---

### Post by kirbyboy on 2008-10-28
I have the struct, here is the code(i don't know much about posting so it won't be pretty inside a source code box):


struct sk_buff {
	/* These two members must be first. */
	struct sk_buff		*next;
	struct sk_buff		*prev;

	struct sock		*sk;
	ktime_t			tstamp;
	struct net_device	*dev;

	struct  dst_entry	*dst;
	struct	sec_path	*sp;

	/*
	 * This is the control buffer. It is free to use for every
	 * layer. Please put your private variables there. If you
	 * want to keep them across layers you have to do a skb_clone()
	 * first. This is owned by whoever has the skb queued ATM.
	 */
	char			cb[48];

	unsigned int		len,
				data_len;
	__u16			mac_len,
				hdr_len;
	union {
		__wsum		csum;
		struct {
			__u16	csum_start;
			__u16	csum_offset;
		};
	};
	__u32			priority;
	__u8			local_df:1,
				cloned:1,
				ip_summed:2,
				nohdr:1,
				nfctinfo:3;
	__u8			pkt_type:3,
				fclone:2,
				ipvs_property:1,
				nf_trace:1;
	__be16			protocol;

	void			(*destructor)(struct sk_buff *skb);
#if defined(CONFIG_NF_CONNTRACK) || defined(CONFIG_NF_CONNTRACK_MODULE)
	struct nf_conntrack	*nfct;
	struct sk_buff		*nfct_reasm;
#endif
#ifdef CONFIG_BRIDGE_NETFILTER
	struct nf_bridge_info	*nf_bridge;
#endif

	int			iif;
#ifdef CONFIG_NETDEVICES_MULTIQUEUE
	__u16			queue_mapping;
#endif
#ifdef CONFIG_NET_SCHED
	__u16			tc_index;	/* traffic control index */
#ifdef CONFIG_NET_CLS_ACT
	__u16			tc_verd;	/* traffic control verdict */
#endif
#endif
	/* 2 byte hole */

#ifdef CONFIG_NET_DMA
	dma_cookie_t		dma_cookie;
#endif
#ifdef CONFIG_NETWORK_SECMARK
	__u32			secmark;
#endif

	__u32			mark;

	sk_buff_data_t		transport_header;
	sk_buff_data_t		network_header;
	sk_buff_data_t		mac_header;
	/* These elements must be at the end, see alloc_skb() for details.  */
	sk_buff_data_t		tail;
	sk_buff_data_t		end;
	unsigned char		*head,
				*data;
	unsigned int		truesize;
	atomic_t		users;
};

You can see there is not a mac member, i'm using 2.6.24-21 now(today updated just when i read your reply so i tried the new), i have the source and i think i have all the soft links that apeared in the faq you send me before.
With uname -r i get: 2.6.24-21-generic

Is some of the soft links wrong?

---

### Post by guedesav on 2008-10-28
No, it seems your kernel simply isn't compatible.

BTW, now that I saw: the issue with linux/config.h is that it's now called linux/autoconf.h. Maybe you want to try again with the other source code provided.

There's a version of the driver(but I'm not sure if this driver actually works or is the same zd1211rw driver) [here]("http://rapidshare.com/files/123648980/ZD1211LnxDrv_2_22_0_0__2_6_24.tar.gz.html"), for kernel 2.6.24.

If it still doesn't work, for now I can only suggest you send the people who wrote the Vendor Based driver an email asking for help. I'll keep trying to figure out a solution.

Good luck.

---

### Post by kirbyboy on 2008-10-28
That's what i put in the first post, i suppose the driver should be updated for newer kernels.  The last time i tried to compile was with the newest kernel.  If you get some answers just tell me, i'll try it too.  Thanks.

---

### Post by guedesav on 2008-10-28
Well, but you can compile it with autoconf. You just have to create a link for it with the name of config.h. My kernel doesn't have config.h, either.

...Unless you have already done that. Then I'll keep looking for something.

---

### Post by fuzzyworbles on 2008-12-17
I've been trying to compile a new zd1211 module also because i need to set it to ad-hoc or master mode, which don't work with the ubuntu included zd1211rw module.

as it turns out, it is broke: [http://launchpadlibrarian.net/11415369/zd1211-source.buildlog.2.6.24-3-generic.1200592871]("http://launchpadlibrarian.net/11415369/zd1211-source.buildlog.2.6.24-3-generic.1200592871")

---

