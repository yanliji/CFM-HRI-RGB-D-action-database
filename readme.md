# UESTC RGB-D Varying-view action database
**UESTC RGB-D Varying-view action database** contains 40 categories of aerobic exercise. We utilized 2 Kinect V2 cameras in 8 fixed directions and 1 round direction to capture these actions with the data modalities of RGB video, 3D skeleton sequences and depth map sequences. 


The camera #1 was fixed in the front view and camera #2 was moved to 7 different views from `d1` to `d7` in different capturing phase. Please refer to Fig1 for more detail. The subjects performed each action for 3 repetitions in a fixed direction. Since there were 7 different views except the front one, we collected 7 pair samples for each subject and each action(a pair sample include the front view and the corresponding side view). What's more, we extra collected the round sample by keeping the subject performing the same action until the capture finished in the round direction. Before each recording, the subjects were told which action to perform and how to perform it, however the detail about the action like the acting style and the acting speed would never be specified.

****

## 1.	Data capture settings
There are 40 different subjects to perform each action and each action is simultaneously captured by camera #1 and camera #2. To enrich our dataset, we adopt three kinds of capture scenarios with different shapes and sizes. Figure 1, 2, and 3 illustrate the layout of cameras and 9 different views(range from `d1` to `d8` and the `front view`) of the capture configurations. When the subjects perform actions, they always face front view camera #1.
### 1.1	The first type of scenario
<div align=center><img width="600" height="480" src="./imgs/fig_The_first_capture_setting.png"/></div>

<div align=center><b>Fig.1 The first capture setting for data collection
</b></div>

Actions' IDs NO.0 -- NO.9 and subjects' IDs NO.01 -- NO.40 are all collected adopting this type of scenario.

### 1.2	The second type of scenario
<div align=center><img width="600" height="480" src="./imgs/fig_The_second_capture_setting.png"/></div>

<div align=center><b>Fig.2 The second capture setting for data collection</b></div>

The table2 in `Action categories and Appendix of capture settings.pdf` shows each subjects' IDs and their actions captured adopting the second scenario.


### 1.3	The third type of scenario

<div align=center><img width="600" height="480" src="./imgs/fig_The_third_capture_setting.png"/></div>

<div align=center><b>Fig 3. The third capture setting for data collection</b></div>

The rest of the actions NO.10 -- NO.39 are captured adopting the third type of scenario. The detail about these actions and subjects’ IDs can be found in `Action categories and Appendix of capture settings.pdf` table3.
In this type of capture scenario, 15 actions are collected by sitting and standing posture, the rest 15 actions are only collected by standing posture. The item with * mark means that the action collected by sitting in `Action categories and Appendix of capture settings.pdf` table3. The ratio of subject that takes sitting posture and standing posture are set to 1:1.


### 1.4	The naming rules of files 
<table>
  <tr>
    <th>Items</th>
    <th>Action categories</th>
    <th>View</th>
    <th>Person</th>
    <th>Front/side view</th>
  </tr>
  <tr>
    <td>For short</td>
    <td>a x</td>
    <td>d x</td>
    <td>p xxx</td>
    <td>c x</td>
  </tr>
  <tr>
    <td>Range</td>
    <td>0~39</td>
    <td>1~7,8</td>
    <td>001~118</td>
    <td>1~2</td>
  </tr>
  <tr>
    <td>Description</td>
    <td>The definition of 40 actions is listed in appendix Table 1.</td>
    <td>1~7: the fixed views
    8: the varying view
    As Fig.1 shows, the front view is annotated with c1.
    </td>
    <td>Person ID</td>
    <td>1: the front view, denote as c1 
		2: the side view and varying view, denote as c2.
	</td>
  </tr>
</table>

For example：
<table border="2" bordercolor="black" width="500" cellspacing="0" cellpadding="5">  
        <tr>  
            <td  rowspan="4"><b>a0_d1_p01_c1</b></td>  
            <td><b>a0</b>: action of punching and knee lifting.</td>  
            <td></td>  
        </tr>  
        <tr>  
            <!--<td>2.1</td>-->  
            <td><b>d1</b>: view 1 </td>  
            <td></td>  
        </tr>  
        <tr>  
            <!--<td>3.1</td>-->  
            <td><b>p01</b>: person ID is 01.</td>  
            <td></td>  
        </tr>  
        <tr>  
            <!--<td>3.1</td>-->  
            <td><b>c1</b>: the data is captured in the front view, and keep synchronized with the sequence of a0_d1_p01_c2.</td>  
            <td></td>  
        </tr>  
</table>  


<table border="2" bordercolor="black" width="500" cellspacing="0" cellpadding="5">  
        <tr>  
            <td  rowspan="4"><b>a0_d1_p01_c2</b></td>  
            <td><b>a0</b>: action of punching and knee lifting.</td>  
            <td></td>  
        </tr>  
        <tr>  
            <!--<td>2.1</td>-->  
            <td><b>d1</b>: view 1 </td>  
            <td></td>  
        </tr>  
        <tr>  
            <!--<td>3.1</td>-->  
            <td><b>p01</b>: person ID is 01.</td>  
            <td></td>  
        </tr>  
        <tr>  
            <!--<td>3.1</td>-->  
            <td><b>c1</b>: the data is captured in the view1 (side view), and keep synchronized with the sequence of a0_d1_p01_c1.</td>  
            <td></td>  
        </tr>  
</table>  

****

## 2	Data modalities

**Note**: In some actions, when we collect side views *ax_d1_px_c2*, *ax_d2_px_c2* and *ax_d3_px_c2* data with camera #2, we also use anthor camera named camera #3 to collect side views *ax_d7_px_c2*, *ax_d6_px_c2* and *ax_d5_px_c2* data at the same time. The data collected from camera1 are named as *ax_d1_px_c1*, *ax_d2_px_c1* and *ax_d3_px_c1*, which means, for each action, except for varying view, there are 7 side view data named *ax_dm_px_c2* (m: range from 1 to 7) and 4 front view data named *ax_dn_px_c1* (n: range from 1 to 4). To keep the integrity of this dataset, we copy data named *ax_d1_px_c1*, *ax_d2_px_c1* and *ax_d2_px_c1* to *ax_d7_px_c1*, *ax_d6_px_c1* and *ax_d5_px_c1*. However the depth files are too large to process like that. Therefore we made a name map for Depth Data which can be found in `namemap.xls`. It can help you to copy the paired data by yourself.

The first column in the `namemap.xls` presents the true name of all files but some of them do not exist. So the second column presents the corresponding existent files that you should refer to supply the miss one in first colume, the third column presents whether files are the same as their true names.

**For the detail, please refer to the file `namemap.xls` in this folder.**

### 2.1  Color AVI (25600 files with size of 81.2GB)
Color videos are in the `RGBvideo/ax_dx_px_cx_color.avi` directory with the video format `.avi` and each frame resolution is 960*540（CV_8UC3, and video frames are synchronized with the Joint Skeleton Frame）.The approximate lengths of each recording in the fixed view and round view are 6 sec and 57 sec respectively.

### 2.2	Skeleton TXT (25600 files with size of 11.7GB)
The skeleton raw files(saved as `.txt` files) are saved in the `skeleton/ax_dx_px_cx_skeleton.txt` directory. We utilized Kinect V2 cameras to record 25 body joints’ coordinates at each frame, each file contains all skeleton frames in one sample. Each skeleton frame is comprised of 76 lines content in txt file.

* **First line** is “#”, “#” is a notation for the start of one joint frame.
* <b>The 2nd to 76th lines</b> are 25 joints of one frame (3D camera space coordinates, color frame point, and depth frame point). 
	- 3D camera space point ends with “0”(unit is m).
	- Color frame point ends with “1”. (unit is pixel)
	- Depth frame point ends with “2”. (unit is pixel)

 

### 2.3	Depth Folder (21509 files with size of 1.34TB)
Depth data is in the `depth/ax_cx_dx_px_depth.tar` directory. These depth images are saved in the format of `.png` with the resolution of 512*424. Depth pixels are saved to unit16 bits.
According to the Kinect SDK document, the high 13-bits in the depth data represent the real value of the depth while the low 3-bits are encoded with user-ID to distinguish the different users. Moreover, the measurement range of the depth acquisition is from 0.5 meters to 4.5 meters with the high precision of 1 millimeter. 

### 2.4	Skeleton MAT (25600 files with size of 5.5GB)
We extra provide the MATLAB `.mat` files for convenience. MATLAB skeleton files(saved as `.mat` files) are restored in the `mat_from_skeleton/ax_dx_px_cx_skeleton.mat` directory. The mats are extracted from skeleton txt files. In one mat file, each row contains one skeleton frame (25 joints) and these joints are described in camera space coordinate. **You can also get your own MAT files using the data prepare script.**

****

## 3. Data download and prepare script
We pack RGB data and skeleton data (txt) respectively. The RGB data file has 80G in size after compressed, so we divide it into several smaller files. The RGB data link is [[Baidu Drive]](https://pan.baidu.com/s/1_pNFIjbxksFWJaUppXzk6A) (extract number: vrb3) and the skeleton data link is [[Baidu Drive]](https://pan.baidu.com/s/1XDOazkGA_rb701DnCJbE4g) (extract number: ldwc).

We also have made all files available on [[Feishu Drive]](https://uestc.feishu.cn/drive/folder/fldcnuOWl00LpKXh2EleOoCaPmd) (extract number: vO2l).

We provide a raw data pre-processing script used to re-format the raw skeleton files , please refer to `scripts/` directory for more detail.

****

## What's more

Please refer to the file `Action categories and Appendix of capture settings.pdf` for more details about the action categories description both in English and Chinese . Before using this database, please make sure you have read `License Agreement.docx` yet. The selected examples of the capturing samples are in the folder `./the example of capturing samples/`.

Anyway, If you have any questions about this database including wishing to evalute your algorithm on this database, feel free to contact us with e-mail [yanliji@uestc.edu.cn](yanliji@uestc.edu.cn). 






