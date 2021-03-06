# ideas & concepts

<!--lint disable list-item-indent-->
<!--lint disable list-item-bullet-indent-->


<div class="hoverswitch">
    <img class="pic" alt="ortogere first sketch 3d model" src="size_papertest/sketch_size_papertest_3d_model.png">
    <img class="pic new" alt="ortogere first sketch 3d model" src="size_papertest/sketch_size_papertest_3d_model_transparent.png">
</div>

<div class="hoverswitch">
    <img class="pic" alt="ortogere paper model white" src="photos/P1660763_small.jpg">
    <img class="pic new" alt="ortogere paper model" src="photos/P1660765_small.jpg">
</div>

---
# Contents
{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---

## main processor
use a [PocketBeagle](https://beagleboard.org/pocket)
some useful hints
-[Ken Shirriff goes hands-on with the PocketBeagle](https://beagleboardfoundation.wordpress.com/2018/02/04/ken-shirrif-goes-hands-on-with-the-pocketbeagle/)
- [Hands-on with the PocketBeagle: a $25 Linux computer with lots of I/O pins](http://www.righto.com/2017/12/hands-on-with-pocketbeagle-tiny-25.html)
- [community capes](https://elinux.org/Beagleboard:BeagleBone_Capes)
- [buy at digikey 21, without USt](https://www.digikey.de/products/de?keywords=PocketBeagle)
- [buy at mouser 25,15€](https://www.mouser.de/_/?Keyword=PocketBeagle)

alternative: [BeagleCore](http://beaglecore.com/) Conrad: ~110€


## concept
till now i had the idea of a direct 1 to 1 connection from the generating high power CPU to the led-drivers.
but it seems that this is very tricky..
i would need high speed connections from the stationary to the rotational part.

so the new concept is to have a 'display driver / frame-buffer'
on option for this could be an [ESP32-WROVER-B](https://docs.espressif.com/projects/esp-idf/en/latest/hw-reference/modules-and-boards.html) [mouser 5€](https://eu.mouser.com/_/?Keyword=ESP32-WROVER-B%20(16MB))
this is an 18x32x4mm module that contains a dual core 240MHz CPU and WiFi and Bluetooth
- [Video animation with ESP32 - example](https://esp32.com/viewtopic.php?f=17&t=6612)
- [PSRAM Write Performance](https://esp32.com/viewtopic.php?p=30649#p30649)
- [example for streaming low-res video: ESP32-OV7670-WebSocket-Camera](https://github.com/mudassar-tamboli/ESP32-OV7670-WebSocket-Camera)


## touch(less) input
buildin / hidden in the top outer edge is a copper surface that acts as electrode.
it is split in 4 parts and managed with an [FDC1004](https://github.com/s-light/TI_FDC1004_Breakout) or similar

this allows for 'hand waving gestures' and approach detection (hopefully ;-) )


## top input rim
[input_rim/](input_rim/)


## compass needle (POV display)

the idea is that the compass needle can rotate slow in both directions to *set* / *point* a direction of choice.

but also can spin up to about 1800rpm (= 30rps) and have LEDs on-top to create a classic POV display.
more details on this aspect can be found in [POV](POV/readme.md)

## wind rose
the printed graphics under the compass needle could also be turned individually -  
that gives a second level of abstraction -

here the idea is to rotate a thin acryl-plate - supported by 3 rollers around.
(where on is powered by a micro dc gear motor or something similar.. )

this needs some sort of indexing - so the thing knows where the disc is currently..

some illumination for this part should be also planned for..

motor for here could be this [700:1 Sub-Micro Planetengetriebemotor 6Dx21L mm](https://www.exp-tech.de/motoren/dc-getriebemotoren/7038/700-1-sub-micro-planetengetriebemotor-6dx21l-mm) one.
its 90RPM@6V

## Lid / Cover
[cover/](cover/)

## communication
the unit should have a W-LAN and / or 433MHz wireless communication link -
so it can be controlled from remote locations to set new values for position or text/image of needle or wind rose

## orientation
best solution would be a GPS + 9DOF inertial measurement unit..
so the thing can report the current absolute location and orientation over the communication channel back to the base and also
be used to route the user to a fixed absolute position (this is in sync with the naming part *Ortus* for *origin*.. )

### sensors
- GNSS / GPS
    - MTK3339
        - [Ultimate GPS Module - 66 channel w/10 Hz updates - MTK3339 chipset ($29.95)](https://www.adafruit.com/product/790)
        - [Adafruit Ultimate GPS Breakout - 66 channel w/10 Hz updates - Version 3 ($39.95)](https://www.adafruit.com/product/746)
        - [Adafruit Ultimate GPS FeatherWing ($39.95)](https://www.adafruit.com/product/3133)
        - [pololu - 66-Channel LS20031 GPS Receiver Module (MT3339 Chipset) $49.95](https://www.pololu.com/product/2138)
        - [sparkfun - GPS Receiver - LS20031 5Hz (66 Channel) $59.95](https://www.sparkfun.com/products/8975)
    - [sparkfun GPS](https://www.sparkfun.com/search/results?term=gps)
    - [sparkfun GPS buying guide](https://www.sparkfun.com/pages/GPS_Guide)
    - Maestro Wireless
        - [Maestro Wireless A5100 GNSS Receiver](http://www.maestro-wireless.com/portfolio-items/a5100-a/) [mouser 17,05€](https://www.mouser.de/_/?Keyword=GNSS%20A5100-A)
            - GPS/GLONASS concurrent GNSS modules
            - Beidou / Galileo ready
            - Pin to pin compatible with A2200-A
            - Low tracking power consumption
        - [Maestro Wireless A5135-H GNSS Receiver with Antenna](http://www.maestro-wireless.com/a5135-h-technical-specifications/)  [mouser 22,10€](https://www.mouser.de/_/?Keyword=GNSS%20A5135-H)
    - [u-blox](https://www.u-blox.de)
        - [CAM-M8Q](https://www.u-blox.com/en/product/cam-m8-series)
            - Concurrent reception of up to 3 GNSS (GPS, Galileo, GLONASS, BeiDou)
            - Miniature size and weight with low power consumption
            - Embedded, omnidirectional and wideband antenna
            - Industry leading –167 dBm navigation sensitivity
            - Optional external antenna
            - Product variants to meet performance and cost requirements
            - [CAM-M8Q-Breakout Multi GNSS Module (GPS, QZSS, GLONASS, BeiDou, Galileo)](https://www.watterott.com/de/CAM-M8Q-Breakout)
        - [NEO-M8P-2](https://www.u-blox.com/en/product/neo-m8p-series)
            - Integrated Real Time Kinematics (RTK) for fast time‑to‑market
            - Smallest, lightest, and energy‑efficient RTK module
            - Complete and versatile solution due to base and rover variants
            - World‑leading GNSS positioning technology
            -  NEO-M8P-2: u-blox M8 high precision module with rover and **base station** functionality
            - GNSS: BeiDou, GLONASS, GPS / QZSS
            - Number of concurrent GNSS: 2
            - List Price:
                - 179 EUR (quantity 1)
                - 106 EUR (quantity >250)
            - [sparkfun GPS-15005 (200$)](https://www.sparkfun.com/products/15005)
        - [ZED-F9P](https://www.u-blox.com/en/product/zed-f9p-module)
            - [u-blox F9: Taking GNSS precision to the next level](https://www.u-blox.com/en/publication/beyond-stories/u-blox-f9-taking-gnss-precision-next-level)
            - Concurrent reception of GPS, GLONASS, Galileo and BeiDou
            - Multi‑band RTK with fast convergence times and reliable performance
            - High update rate for highly dynamic applications
            - Centimeter accuracy in a small and energy efficient module
            - Easy integration of RTK for fast time‑to‑market
            - GNSS: BeiDou, **Galileo**, GLONASS, GPS / QZSS
            - Number of concurrent GNSS: 4
            - available end of November 2018 ? (currently only engineering samples)
            - List Price:
                - ? guess 200 EUR (quantity 1)
                - ? EUR (quantity >250)
            - [simpleRTK2B](https://www.ardusimple.com/simplertk2b/)
            - [simpleRTK2B - Basic Kit (213€)](https://www.kickstarter.com/projects/simplertk2b/simplertk2b-the-first-multiband-rtk-shield-based-o)

- IMU
    - [pololu UM7-LT Orientation Sensor](https://www.pololu.com/product/2763) [exp-tech 129,95€](https://www.exp-tech.de/sensoren/imu/5999/um7-lt-orientierungssensor)
    - [BNO055](https://www.bosch-sensortec.com/bst/products/all_products/bno055)
        - [Adafruit 9-DOF Absolute Orientation IMU Fusion Breakout - BNO055](https://www.adafruit.com/product/2472) [exp-tech 35,35€](https://www.exp-tech.de/sensoren/beschleunigung/6446/adafruit-9-dof-absolute-orientation-imu-fusion-breakout-bno055?c=1090)
        - [BNO055 Absolute Orientation Sensor with Raspberry Pi & BeagleBone Black](https://learn.adafruit.com/bno055-absolute-orientation-sensor-with-raspberry-pi-and-beaglebone-black)
    - [BNO080](https://www.bosch-sensortec.com/bst/products/all_products/bno080)
        - [Qwiic VR IMU (BNO080) Hookup Guide](https://learn.sparkfun.com/tutorials/qwiic-vr-imu-bno080-hookup-guide?_ga=2.203024980.490365886.1525245502-1455689428.1519465931) [exp-tech 33,68€](https://www.exp-tech.de/sensoren/beschleunigung/8757/sparkfun-vr-imu-breakout-bno080-qwiic?c=1090)
    - [this project](https://hackaday.io/project/39158-odroid-xu4-based-control-computer) mentions that the BNO080 is more stable / less noisy


## power
in the bottom of the unit needs to be place for some LiPo / LiFe cells...
if the housing is made with an inner width of 180mm (the outer width of the paper model)
then two 2s1p inline LiFePo4 packs with 26650 form-factor can fit in the bottom..

most power hungry is the POV section.. more details there..
