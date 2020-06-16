---
title: "bag pcd 라이다 데이터 kitti(bin) 포맷 변환"
date: 2020-06-08 08:26:28 -0400
categories: bag2bin bag2pcd pcd2bin bag2kitti pcd bin kitti
---

0.준비사항
　
0.0 우분투에 ros 설치
(http://wiki.ros.org/ROS/Installation)
　
0.1 bag파일 업로드
bag파일을 ros가 설치된 서버에 업로드

　

1.bag2pcd

1.0 명령창에서 bag2pcd 명령 실행

`rosrun pcl_ros bag_to_pcd 파일경로 /lidar_cloud0 ./pcd`

예시)

`rosrun pcl_ros bag_to_pcd /home/lidartoeverything/CES_11_30.bag /lidar_cloud0 ./pcd`



2.pcd2bin (kitti)

2.0 rosbag2kitti 코드 다운로드 
(https://github.com/leofansq/Tools_RosBag2KITTI)

2.1
프로젝트 만들기
`mkdir CMakeFile; cd CMakeFile; cmake ..; make`

2.2 코드 폴더 안의 pcd2bin.cpp 파일에서 경로 고치기
pcd2bin폴더 안의 pcd2bin.cpp 코드 내 int main 부분의 bin_path 와 pcd_path를 현재에 맞게 변경

pcd2bin.cpp 내 하단 부분의 경로 수정 

`    std::string bin_path = "/home/cecilia/leo_projects/bishe2019/pcd2bin/bin/";`

`    std::string pcd_path = "/home/cecilia/leo_projects/bishe2019/pcd2bin/pcd/";`

2.3 변환하고자 하는 pcd파일을 다운로드 받은 pcd폴더에 넣기

2.4 CMake를 이용한 변환

`cd CMakeFile; ./pcd2bin`


3.파일 리스트 만들기

3.0 list.txt 만들기

`cd bin; ls -1 | grep ".bin$" > list.txt`

3.1 files_list.txt 만들기

`python get_list.py`


#.참조
https://github.com/leofansq/Tools_RosBag2KITTI
