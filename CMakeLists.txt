cmake_minimum_required(VERSION 3.0.2)
project( frif )

# Find OpenCV library
FIND_PACKAGE(OpenCV REQUIRED) # OpenCV 3
#FIND_PACKAGE(OpenCV 2 REQUIRED) # OpenCV 2
include_directories(${OpenCV_INCLUDE_DIRS})

###########
## Build ##
###########

set(FRIF_SRC ./)


# add core libs
FILE(GLOB frif_lib ${FRIF_SRC}/FrifDetector.cpp ${FRIF_SRC}/FrifDescriptor.cpp ${FRIF_SRC}/utils.cpp )

add_library( frif_lib ${frif_lib})

#set(TYPES_SBA_EXTENSION_LIB frif_lib)

ADD_EXECUTABLE(frif main.cpp)
TARGET_LINK_LIBRARIES(frif  ${OpenCV_LIBRARIES} frif_lib)
