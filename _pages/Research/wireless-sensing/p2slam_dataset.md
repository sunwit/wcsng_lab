---
title: "WCSNG - Research"
layout: gridlay
excerpt: "P2SLAM dataset"
sitemap: true
permalink: /p2slam/
---

### P2SLAM: Bearing based WiFi SLAM for Indoor Robots
```
Authors: Aditya Arun, Roshan Ayyalasomayajula, William Hunter, Dinesh Bharadia
```


<div class="well">
 <center>
 <h4><A href="#env">Environment Description</A>&emsp;<A href="#result">In-depth Results</A>&emsp;<A href="#swapc">SWaP-C Analysis</A>&emsp;<A href="#cite">Citation</A> &emsp;<a href="{{ site.url }}{{ site.baseurl }}/files/p2slam.pdf" target="_blank"> Paper download [PDF] </a> </h4>
 </center>
</div>

---

<div class="row">
<div class="col-sm-5 clearfix">
<br>
<div class="well">
<h3 id="abstract">Abstract</h3>
<p align="justify">
A recent spur of interest in indoor robotics has increased the importance of robust simultaneous localization and mapping algorithms in indoor scenarios. This robustness is typically provided by the use of multiple sensors which can correct each others’ deficiencies. In this vein, exteroceptive sensors, like cameras and LiDAR’s, employed for fusion are capable of correcting the drifts accumulated by wheel odometry or inertial measurement units (IMU’s). However, these exteroceptive sensors are deficient in highly structured environments and dynamic lighting conditions. This letter will present WiFi as a robust and straightforward sensing modality capable of circumventing these issues. Specifically, we make three contributions. First, we will understand the necessary features to be extracted from WiFi signals. Second, we characterize the quality of these mea  surements. Third, we integrate these features with odometry into a state-of-art GraphSLAM backend. We present our results in a 25×30 m and 50×40 environment and robustly test the system by driving the robot a cumulative distance of over 1225 m in these two environments. We show an improvement of at least 6× compared odometry-only estimation and perform on par with one of the state-of-the-art Visual-based SLAM.
</p>
</div>
<br>
</div>

<div class="col-sm-7 clearfix">
<h3 id="idea">High-level idea</h3>
The following video gives a high-level idea on how the Wi-Fi bearing measurements are made. It also shows when the measurements are dropped to have robust measurements.
<iframe width="100%" height="267" src="https://www.youtube.com/embed/0is2C4l_QfM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
The robots movement over three timestamp are shown. Relative odometry is measured between two consecutive robot poses. At each timestamp, the robot ping’s an AP (orange arrow) and receives a pong reply (green arrow). For each ping and pon transmission the AP-sided and Robot-sided bearing of the signal is computed respectively. These measurements can then be fed into GTSAM for accurate drift correction and to recover the robot's trajectory.
<div class="row">
<div class="col-sm-6 clearfix">
<a href="{{ site.url }}{{ site.baseurl }}/images/pubpic/p2slam.png"><center><img src="{{ site.url }}{{ site.baseurl }}/images/pubpic/p2slam.png" width="100%" style="float:center" ></center> </a>
</div>
<div class="col-sm-6 clearfix">
<a href="{{ site.url }}{{ site.baseurl }}/images/pubpic/p2slam.png"><center><img src="{{ site.url }}{{ site.baseurl }}/images/pubpic/p2slam-graph.png" width="100%" style="float:center" ></center> </a> <br>
</div>
</div>
</div>
</div>

---
<h3 id="env">Envrionment Description</h3>

<div class="row">
<div class="col-sm-6 clearfix">
<br>
<p align="justify"> 
  Here we describe the environments and the datasets collected in these environments. We further showcase P2SLAM results as compared to camera-based baseline RTABMap. We find that in all datasets inclusion of WiFi-based sensing for localization performs on par with RTABMap and makes a strong case for the inclusion of these simple sensors within SLAM systems. 
</p>
</div>
<br>
<div class="col-sm-6 clearfix">
<div class="videoWrapper">
<iframe width="100%" height="230" src="https://www.youtube.com/embed/SJ4I1VJ0gFs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
</div>
</div>


1.  <b> Env-1: Atkinson Hall 4th Floor </b> -- 20 x 30 m (65 x 100 feet) standard office environment with complex mulitpath and mulitple Non-line of sight conditions. A total of 5 AP's were deployed in this environment and two paths (<i> Dataset 1 </i> and <i> Dataset 2 </i>) were taken as described below.
<a href="{{ site.url }}{{ site.baseurl }}/images/respic/env1.jpg"><img src="{{ site.url }}{{ site.baseurl }}/images/respic/env1.jpg" width="100%" style="float: center" > </a>

2. <b> Env-2: Atkinson Hall Ground Floor </b> -- 50 x 40 m large environment covering mulitple corridors and large lobbies and auditorium spaces. <i> Dataset 3 </i> was collected in this environment.
<a href="{{ site.url }}{{ site.baseurl }}/images/respic/env2.jpg"><img src="{{ site.url }}{{ site.baseurl }}/images/respic/env2.jpg" width="95%" style="float: center" > </a>

<p> First, we summarize all our results in the following table. We show the median and 90th percentile translation and orientation errors in centimeters and degrees respectively. We show across three sensing modalities -- using odometry only, using odometry + Camera (RTABMap) and using odometry + WiFi (P2SLAM): </p>

<!-- Results table -->
<center>
    <style type="text/css">
        .tg  {border-collapse:collapse;border-spacing:0;}
        .tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
          overflow:hidden;padding:10px 5px;word-break:normal;}
        .tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
          font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
        .tg .tg-kwiq{border-color:inherit;color:#000000;text-align:left;vertical-align:top}
        .tg .tg-vpkt{border-color:inherit;color:#000000;font-weight:bold;text-align:center;vertical-align:top}
        .tg .tg-21f3{border-color:inherit;color:#000000;font-weight:bold;text-align:left;vertical-align:top}
        .tg .tg-ml2k{border-color:inherit;color:#000000;text-align:center;vertical-align:top}
    </style>
    <table class="tg">
        <thead>
          <tr>
            <th class="tg-kwiq" rowspan="3"><br><br><br><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Sensors</span></th>
            <th class="tg-vpkt" colspan="2"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Env 1 - Dataset 1</span></th>
            <th class="tg-vpkt" colspan="2"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Env 1 - Dataset 2</span></th>
            <th class="tg-vpkt" colspan="2"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Env 2 - Dataset 3</span></th>
          </tr>
          <tr>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Trans </span><br><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">(cm)</span></th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Orient </span><br><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">(deg)</span></th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Trans </span><br><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">(cm)</span></th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Orient </span><br><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">(deg)</span></th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Trans </span><br><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">(cm)</span></th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Orientation </span><br><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">( </span><span style="font-style:normal;text-decoration:none;background-color:transparent">deg</span><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">)</span></th>
          </tr>
          <tr>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">Med</span><br>(90th)</th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none">Med</span><br>(90th)</th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none">Med</span><br>(90th)</th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none">Med</span><br>(90th)</th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none">Med</span><br>(90th)</th>
            <th class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none">Med</span><br>(90th)</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td class="tg-21f3">Dead reckoning</td>
            <td class="tg-ml2k"><span style="background-color:transparent">180.6</span><br>(<span style="text-decoration:none;background-color:transparent">513.9</span>)</td>
            <td class="tg-ml2k"><span style="background-color:transparent">8.64</span><br>(<span style="text-decoration:none;background-color:transparent">18.1</span>)</td>
            <td class="tg-ml2k"><span style="background-color:transparent">378.6</span><br>(<span style="text-decoration:none;background-color:transparent">1156</span>)</td>
            <td class="tg-ml2k"><span style="background-color:transparent">23.35</span><br><span style="background-color:transparent">(</span><span style="text-decoration:none;background-color:transparent">37</span><span style="background-color:transparent">)</span></td>
            <td class="tg-ml2k"><span style="background-color:transparent">422</span><br>(<span style="text-decoration:none;background-color:transparent">1098</span>)</td>
            <td class="tg-ml2k"><span style="background-color:transparent">16</span><br>(<span style="text-decoration:none;background-color:transparent">30.5</span>)</td>
          </tr>
          <tr>
            <td class="tg-21f3">RTABMap</td>
            <td class="tg-ml2k"><span style="background-color:transparent">36.8</span><br>(<span style="text-decoration:none;background-color:transparent">165.7</span>)</td>
            <td class="tg-ml2k"><span style="background-color:transparent">2.97</span><br>(<span style="text-decoration:none;background-color:transparent">10.83</span>)</td>
            <td class="tg-ml2k"><span style="font-weight:bold">38.5</span><br><span style="font-weight:bold">(63.7)</span></td>
            <td class="tg-ml2k"><span style="font-weight:bold">0.74</span><br><span style="font-weight:bold">(2.69)</span></td>
            <td class="tg-ml2k"><span style="font-weight:bold">61.5</span><br>(256)</td>
            <td class="tg-ml2k"><span style="background-color:transparent">2.2</span><br>(<span style="text-decoration:none;background-color:transparent">7.99</span>)</td>
          </tr>
          <tr>
            <td class="tg-21f3"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">P</span>2<span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">SLAM</span></td>
            <td class="tg-vpkt"><span style="font-style:normal;text-decoration:none;background-color:transparent">26.9</span><br>(<span style="font-style:normal;text-decoration:none;background-color:transparent">54.7</span>)</td>
            <td class="tg-vpkt"><span style="font-weight:700;font-style:normal;text-decoration:none;background-color:transparent">1.28</span><br>(<span style="font-style:normal;text-decoration:none;background-color:transparent">3.16</span>)</td>
            <td class="tg-ml2k">40.4<br>(76.9)<br></td>
            <td class="tg-ml2k"><span style="font-style:normal;text-decoration:none;background-color:transparent">1.32</span><br>(3.7)</td>
            <td class="tg-ml2k"><span style="font-style:normal;text-decoration:none;background-color:transparent">65.2</span><br><span style="font-weight:bold">(158)</span></td>
            <td class="tg-ml2k"><span style="font-weight:bold;font-style:normal;text-decoration:none;background-color:transparent">1.65</span><br><span style="font-weight:bold">(</span><span style="font-weight:bold;font-style:normal;text-decoration:none;background-color:transparent">3.95</span><span style="font-weight:bold">)</span></td>
          </tr>
        </tbody>
    </table>
</center>

---

<h3 id="result">In-depth Results</h3>


Next, we present in-depth analysis for the above three datasets. Further details to use this dataset is given below. 

1. <b> Env 1 - Dataset 1 </b> (easy): Simple robot movement where we traverse all the corridors, for a total path length of 330 m (approx) at 18 cm/s. AP's are placed in the locations marked by circles in the above figure. 
<!-- Download the dataset .mat file [here](https://ucsdcloud-my.sharepoint.com/:u:/g/personal/aarun_ucsd_edu/EZBHoXwnUGBBgx1X-2G0g-YBpJCzFOyaEhYuwL5SShRNJA?e=3oiN1A). -->
<a href="{{ site.url }}{{ site.baseurl }}/images/respic/results_ds1.jpg"> <center> <img src="{{ site.url }}{{ site.baseurl }}/images/respic/results_ds1.jpg" width="50%" style="float: center" > </center> </a>

2. <b> Env 1 - Dataset 2 </b> (hard): Complex robot movement where the robot traverses different nooks in the environment. This path closely replicate one taken by a vacuume cleaner or package delivery robot. Total path-length travelled is 495 m (approx) at 28 cm/s. AP's are placed in the locations marked by cross in the above figure. 
<!-- Download the dataset .mat file [here](https://ucsdcloud-my.sharepoint.com/:u:/g/personal/aarun_ucsd_edu/Ef1ETWRODuxEj4RSAV-wlK4BfirvThNOviIqoYJxQalmyg?e=PBCH50). -->
<a href="{{ site.url }}{{ site.baseurl }}/images/respic/results_ds2.jpg"> <center> <img src="{{ site.url }}{{ site.baseurl }}/images/respic/results_ds2.jpg" width="50%" style="float: center" > </center> </a>

3. <b> Env 2 - Dataset 3 </b>: Simple robot movement where mulitple corridors are traversed at 28 cm/s for a total path length of 400 m (approx). 
<!-- Download the dataset .mat file [here](https://ucsdcloud-my.sharepoint.com/:u:/g/personal/aarun_ucsd_edu/EVPUpb8DFuRBoKW8r7yS7nkBRWXWP9Z03eQcX7O4XydnEg?e=9j93j4). -->
<a href="{{ site.url }}{{ site.baseurl }}/images/respic/results_ds3.jpg"> <center> <img src="{{ site.url }}{{ site.baseurl }}/images/respic/results_ds3.jpg" width="50%" style="float: center" > </center> </a>

---

<h3 id="swapc">SWaP-C Analysis</h3>

SWaP-C is a common industry acronym for Size, Weight, Power and Cost. In P2SLAM, we show the efficacy of WiFi-based sensing for robotic localization and navigation. Furthermore, we claim that the SWaP-C metrics for WiFi radios is 10 times better than LiDAR's. Here we further justify this claim. 

<h4> Size </h4>

The smallest surround LIDAR, [Puck Lite](https://www.mapix.com/wp-content/uploads/2018/07/63-9286_Rev-H_Puck-LITE_Datasheet_Web.pdf) by Velodyne Lidar, has a very small form factor with a 3.5" diameter and height of 2.82". 

Developing a WiFi sensor using the [ESP8266 NodeMCU](https://www.nodemcu.com/index_en.html) with multi-antenna capability will have dimensions of (2" x 1" x 0.5"), with the size of an 4-element linear antenna array at 9.8" or a square antenna array at 6.25". 

<h4> Weight </h4>

The Puck Lite weighs at 590 g. An ESP8266-based design would weight a meagre 9 g. 

<h4> Power </h4>

<!-- Power table -->
<center>
    <style type="text/css">
    .tg  {border-collapse:collapse;border-spacing:0;}
    .tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
      overflow:hidden;padding:10px 5px;word-break:normal;}
    .tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
      font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
    .tg .tg-8efc{background-color:#c0c0c0;border-color:inherit;color:#000000;font-size:100%;font-weight:bold;text-align:center;
      vertical-align:top}
    .tg .tg-f35e{background-color:#c0c0c0;border-color:inherit;font-size:100%;font-weight:bold;text-align:left;vertical-align:top}
    .tg .tg-kwiq{border-color:inherit;color:#000000;text-align:left;vertical-align:top}
    .tg .tg-1pgq{background-color:#c0c0c0;border-color:inherit;color:#000000;font-size:100%;font-weight:bold;text-align:left;
      vertical-align:top}
    .tg .tg-ml2k{border-color:inherit;color:#000000;text-align:center;vertical-align:top}
    .tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
    .tg .tg-vpkt{border-color:inherit;color:#000000;font-weight:bold;text-align:center;vertical-align:top}
    .tg .tg-21f3{border-color:inherit;color:#000000;font-weight:bold;text-align:left;vertical-align:top}
    .tg .tg-fymr{border-color:inherit;font-weight:bold;text-align:left;vertical-align:top}
    </style>
    <table class="tg">
    <thead>
      <tr>
        <th class="tg-8efc">Device</th>
        <th class="tg-8efc">Power Consumption</th>
        <th class="tg-1pgq">Notes</th>
        <th class="tg-f35e"><span style="color:#000">Sources</span></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="tg-ml2k">Hokoyo Lidar</td>
        <td class="tg-ml2k">8.4 W</td>
        <td class="tg-kwiq">Single channel</td>
        <td class="tg-0pky"><a href="https://autonomoustuff.com/-/media/Images/Hexagon/Hexagon%20Core/autonomousstuff/pdf/hokuyo-utm-30lx-datasheet.ashx?la=en&hash=E1F8A1F837A229BD9EB3FEC17DD3488F" target="_blank" rel="noopener noreferrer">Datasheet</a></td>
      </tr>
      <tr>
        <td class="tg-vpkt">Velodyne Puck</td>
        <td class="tg-vpkt">8 W</td>
        <td class="tg-21f3">16 channel</td>
        <td class="tg-fymr"><a href="https://www.mapix.com/wp-content/uploads/2018/07/63-9286_Rev-H_Puck-LITE_Datasheet_Web.pdf" target="_blank" rel="noopener noreferrer">Datasheet</a></td>
      </tr>
      <tr>
        <td class="tg-ml2k">ASUS RT-AC86U</td>
        <td class="tg-ml2k">Measured @ 6.5 W in lab</td>
        <td class="tg-kwiq">802.11AC, 5 Ghz, 20/40/80 MHz, 4x4</td>
        <td class="tg-0pky"></td>
      </tr>
      <tr>
        <td class="tg-ml2k">Quantenna </td>
        <td class="tg-ml2k">Measured @ 3.2 W in lab</td>
        <td class="tg-kwiq">802.11AC, 5 Ghz, 20/40/80 MHz,  4x4</td>
        <td class="tg-0pky"></td>
      </tr>
      <tr>
        <td class="tg-ml2k">Intel 5300</td>
        <td class="tg-ml2k">1.6 W Rx, 2.1 W Tx</td>
        <td class="tg-kwiq">802.11n, 2.4 Ghz, 20 and 40 MHz, <br>3x3</td>
        <td class="tg-0pky"><a href="https://www.usenix.org/legacy/events/hotpower/tech/full_papers/Halperin.pdf" target="_blank" rel="noopener noreferrer">Power measurements by Halperin et al.</a></td>
      </tr>
      <tr>
        <td class="tg-ml2k">TP-Link TL-WDR4300<br>(Atheros CSI tool)</td>
        <td class="tg-ml2k">4.6 W</td>
        <td class="tg-kwiq">IEEE 802.11n, 2.4 GHz, 20/40 MHz, 3x3 </td>
        <td class="tg-kwiq"><a href="http://www.tpcdb.com/product.php?id=1729" target="_blank" rel="noopener noreferrer">Power consumption database</a></td>
      </tr>
      <tr>
        <td class="tg-vpkt">ESP 32, NodeMCU</td>
        <td class="tg-vpkt">240 mW x 4 ~ 1 W</td>
        <td class="tg-21f3">802.11 b/g/n, 2.4 GHz, 20 MHz</td>
        <td class="tg-21f3"><a href="https://jeelabs.org/book/1526f/" target="_blank" rel="noopener noreferrer">Measurement by JeeLabs</a></td>
      </tr>
    </tbody>
    </table>
</center>

From the above table, we can see that taking a conservative power estimate of the NodeMCU, we find the power consumption to be close to 1 W, which is about 8 times lower than the Velodyne Puck Lite. 

<h4> Cost </h4>

Publicly available information about the Velodyne Puck prices the it at $8000. A simple NodeMCU WiFi sensor would cost less than $20. 

---

<h3 id="usage">Dataset Usage</h3>


The CSI data is named as **channels.mat** and the rosbag is named as **data.bag** in the resepctive dataset folders. All the datasets can be downloaded [here (size: 19.6 GB)](https://ucsdcloud-my.sharepoint.com/:u:/g/personal/aarun_ucsd_edu/Ed8UkFdFa71AqorqwJM-ESkBPJaC8z18bSKXob4A29K14A). To access the dataset, you will need to fill out a brief <a href="https://forms.gle/UgUQ5XkhVLqE9FEj6" target="_blank">Google Form</a> to agree to the terms of usage. Upon form completion an email will be sent out with the download instructions. 

The MATLAB files (channels.mat) are stored using **HDF5** file structure and contain the following variables:
- **channels_cli**: *[ n_datapoints x n_frequency x n_ap x n_rx_ant X n_tx_ant]* 5D complex channel matrix recieved at the WiFi access points deployed in the environment.
- **channels_ap**: *[ n_datapoints x n_frequency x num_aps x n_rx_ant X n_tx_ant]* 5D complex channel matrix recieved at the WiFi access point present on the robot.
- **cli_rssi_synced**: *[ n_datapoints x n_rx_ant x n_ap ]* Recieved signal strength matrix at the environments' WiFi access point.
- **ap_rssi_synced**: *[ n_datapoints x n_rx_ant x n_ap ]* Recieved signal strength matrix at the robot's WiFi access point.
- **cli_hw_noise_synced**: *[ n_datapoints x n_ap ]* Hardware noise floor measured at the Environment's AP's when signal is received from the robot.
- **ap_hw_noise_synced**: *[ n_datapoints x n_ap ]* Hardware noise floor measured at robot' WiFi AP with signal received from each of the environment's AP's.
- **ap**: *[1 x n_ap]* cell matrix. Each element corresponding to *[ n_rx_ant x 2]* antenna positions in th global coordinates.  
- **labels**: *[ n_datapoints x 3 ]* 2D best-estimate ground truth XY labels + heading of the robot -- computed using Cartographer using onboard Lidar and internal odometry.
- **labels_noise**: *[ n_datapoints x 3 ]* 2D XY labels + heading of the robot computed using only robot's wheel encoder (highly erroneous measurements)
- **labels_imu**: *[ n_datapoints x 3 ]* 2D  XY labels + heading of the robot computed using the robot's wheel encoder and internal gyroscope (less erroneous than only using wheel encoders)
- **labels_vel**: *[ n_datapoints x 1 ]* Velocity of the robot in m/s.

The rosbags (data.bag) contain the following topics:

1. **Camera Information from Intel Realsense D415. DS 1 uses the Orbbec Astra camera and its topics are in parantheses**:
- /camera/color/camera_info (/camera/rgb/camera_info)
- /camera/color/image_raw/compressed (/camera/rgb/image_rect_color/compressed)
- /camera/depth_registered/image_raw/compressedDepth (/camera/depth_registered/image_raw/compressedDepth)

2. **Odometry Information from Turtlebot base**:
- /mobile_base/sensors/core
- /mobile_base/sensors/imu_data
- /mobile_base/sensors/imu_data_raw
- /odom
- /tf

3. **Hokuoyo Lidar scan information**:
- /scan

---

<h3 id="cite">Citation</h3>
If you found our work useful, please cite the project as :

@ARTICLE{9691786,
  author={Arun, Aditya and Ayyalasomayajula, Roshan and Hunter, William and Bharadia, Dinesh}, <br>
  journal={IEEE Robotics and Automation Letters},  <br>
  title={P2SLAM: Bearing Based WiFi SLAM for Indoor Robots}, <br>
  year={2022}, <br>
  volume={7}, <br>
  number={2}, <br>
  pages={3326-3333}, <br>
  doi={10.1109/LRA.2022.3144796}} <br>

<!-- ## Downloads ##
 -->

<!-- ### Channel Downloads:


Individual Downloads:
- [channels_atk_ds1](https://ucsdcloud-my.sharepoint.com/:u:/g/personal/aarun_ucsd_edu/EZBHoXwnUGBBgx1X-2G0g-YBpJCzFOyaEhYuwL5SShRNJA?e=3oiN1A)
- [channels_atk_ds2](https://ucsdcloud-my.sharepoint.com/:u:/g/personal/aarun_ucsd_edu/Ef1ETWRODuxEj4RSAV-wlK4BfirvThNOviIqoYJxQalmyg?e=PBCH50)
- [channels_atk_ds3](https://ucsdcloud-my.sharepoint.com/:u:/g/personal/aarun_ucsd_edu/EVPUpb8DFuRBoKW8r7yS7nkBRWXWP9Z03eQcX7O4XydnEg?e=9j93j4)
 -->

<!-- #### All the dataset downloads are **PASSWORD** protected. To get the password, please read and agree to the [terms and conditions](https://forms.gle/WWGymUFxhPWRc4zu7). You can then proceed to download datasets from the links above. -->

<!-- 
## CITATION ##

- TBA -->

  
