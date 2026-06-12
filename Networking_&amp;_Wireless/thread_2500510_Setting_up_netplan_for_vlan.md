---
title: "Setting up netplan for vlan"
date: 2024-09-04
forum: Networking &amp; Wireless
---

### Post by thor2605 on 2024-09-04
Hi there,

I want to setup my ubuntu server for vlan usage.

So my netplan looks like this:

```

[COLOR=#000000]**network****:**
    **version****:** 2
    **ethernets****:**
        **enp1s0****:**
            **dhcp4****: yes**
    **vlans****:**
        **enp1s0.20:**
            **id****:** 20
            **link****:** enp1s0
[/COLOR][B]        enp1s0.20:
[/B][COLOR=#000000][FONT=var(--font-stack--monospace)]**            id**[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)]**:**[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)] 20
[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)]**            link**[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)]**:**[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)]enp1s0[/FONT][/COLOR]
```

Now I want to configure the routing and read about routes and routing-policy.
My first try to add rt_tables for each interface and changing the netplan as follow:

```

[COLOR=#000000]**network****:**
    **version****:** 2
    **ethernets****:**
        **enp1s0****:**
            **dhcp4**[B]: no
[/B]            **addresses**: [172.16.1.10/24]
            **routes**:
              - **to**: 0.0.0.0/0
                **via**: 172.16.1.1
                **table**: 201
            **routing-policy**:
              - **from**: 172.16.1.0/24
                **table**: 201
    **vlans****:**
        **enp1s0.20:**
            **id****:** 20
            **link****:** enp1s0[/COLOR]
[COLOR=#000000]            **routes**:
              - **to**: 0.0.0.0/0
                **via**: 172.16.20.1
                **table**: 202
            **routing-policy**:
              - **from**: 172.16.20.0/24
                **table**: 202[/COLOR][B]        
         enp1s0.30:[/B][COLOR=#000000][FONT=var(--font-stack--monospace)][B]           
             id[/B][/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)]**:**[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)] 30[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)][B]            
             link[/B][/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)]**:**[/FONT][/COLOR][COLOR=#000000][FONT=var(--font-stack--monospace)]enp1s0[/FONT][/COLOR][COLOR=#000000]            
**             routes**:
                - **to**: 0.0.0.0/0
                  **via**: 172.16.30.1
                  **table**: 203
             **routing-policy**:
                - **from**: 172.16.30.0/24
                  **table**: 203[/COLOR]
```

I don't need ip addresses in the vlan, because I run a docker with macvlan internally.

But now I can't access my ubuntu server anymore. SSH isn't working.

What I am doing wrong here?

---

