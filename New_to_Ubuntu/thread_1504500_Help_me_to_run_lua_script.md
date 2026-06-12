---
title: "Help me to run lua script"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-08
can some tell me how to run this lua script,

```

--[[
By junoon53
    Based on observer.lua by mrsnail.
        Based on the superb script, Ring Meters by londonali1010. Big thanks!
    
Original notes:
/This script draws percentage meters as rings. It is fully customisable; all options are described in the script.
/
/IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement near the end of the script uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
/


To call this script in Conky, use the following (assuming that you save this script to ~/scripts/observer.lua):
    lua_load ~/scripts/observer.lua
    lua_draw_hook_pre ring_stats
]]
-- Settings table for rings:
settings_table = {

    {
        name='downspeedf',
        arg='',
        max=500,
        bg_colour=0xffffff,
        bg_alpha=0.15,
        fg_colour=0xFFBB00,
        fg_alpha=0.0,
        x=100, y=100,
        radius=50,
        thickness=10,
        start_angle= 10,
        end_angle=360,
        motion=1
    },
    {
        name='upspeedf',
        arg='',
        max=500,
        bg_colour=0xffffff,
        bg_alpha=0.15,
        fg_colour=0xFFBB00,
        fg_alpha=0.0,
        x=100, y=100,
        radius=70,
        thickness=10,
        start_angle= 10,
        end_angle=360,
        motion=-1
    },
    {
        name='cpu',
        arg='cpu0',
        max=500,
        bg_colour=0xF75B5B,
        bg_alpha=0.75,
        fg_colour=0xFFBB00,
        fg_alpha=0.0,
        x=100, y=100,
        radius=90,
        thickness=10,
        start_angle= 0,
        end_angle=60,
        motion=1
    },
    {
        name='cpu',
        arg='cpu0',
        max=500,
        bg_colour=0xF75B5B,
        bg_alpha=0.75,
        fg_colour=0xFFBB00,
        fg_alpha=0.0,
        x=100, y=100,
        radius=90,
        thickness=10,
        start_angle= 120,
        end_angle=180,
        motion=1
    },
    {
        name='cpu',
        arg='cpu0',
        max=500,
        bg_colour=0xF75B5B,
        bg_alpha=0.75,
        fg_colour=0xFFBB00,
        fg_alpha=0.0,
        x=100, y=100,
        radius=90,
        thickness=10,
        start_angle= 240,
        end_angle=300,
        motion=1
    },
    
}


require 'cairo'

function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
    
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)

    -- Draw background ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end



function conky_ring_stats()

    -- The somewhat modified setup_rings function.
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        if value == nil then value = 0 end
        pct=value/pt['max']
    
        --This code does the rotation. Pretty simple addition.
        
        if pt['motion']>0 then pt['start_angle'],pt['end_angle']=pt['start_angle']+value/50,pt['end_angle']+value/50
        end
        if pt['motion']<0 then pt['start_angle'],pt['end_angle']=pt['start_angle']-value/50,pt['end_angle']-value/50
        end
        
        --This keeps the values around 0...360
        if pt['end_angle']<0 then --for CCW rotation,
            pt['start_angle'],pt['end_angle']=pt['start_angle']+360,pt['end_angle']+360
            end
            
        if pt['end_angle']>360 then --and for CW rotation.
            pt['start_angle'],pt['end_angle']=pt['start_angle']-360,pt['end_angle']-360
            end
    
        draw_ring(cr,pct,pt)
    end
        

    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
        
        
    end

end
```

---

### Post by Diabolis on 2010-06-12
This Lua script is meant to be run by Conky. The original script was written by londonali1010 and this one is missing all the comments:

> 
You can tweak the settings_table below to suit your preferences.  You can draw
as many pies as you want, by simply adding more entries in the settings_table.

Load this in your conkyrc like so (assuming you save this script to
~/cairo_pie.lua):

lua_load ~/cairo_pie.lua
lua_draw_hook_pre pie_time
lua_draw_hook_post cairo_cleanup


My version:
[URL="http://www.flickr.com/photos/silvag/4126357194/in/set-72157604983185232/"]
[IMG]http://farm3.static.flickr.com/2572/4126357194_eed4e264fe_m.jpg[/IMG]
[/URL]

---

