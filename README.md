# Car Bidding Platform

## **Live At: https://thunderous-treacle-c9f408.netlify.app**

<img width="1680" alt="Screenshot 2023-04-25 at 9 54 50 AM" src="https://user-images.githubusercontent.com/67619547/234282788-81bdd9dc-9f70-4b42-b1c4-0f2b7cfd9fe2.png">

### **About application**

BidMyRide is a virtual car auction platform that provides an opportunity for both buyers and sellers to engage in the purchasing and selling of cars online. The platform offers a real-time bidding process, allowing users to browse available cars, place bids, and compare different cars based on their features and specifications. The platform also provides a comprehensive transaction history, allowing users to track their buying and selling activities.

### **Target User Insights**

Bid My Ride is targeted towards a wide range of users:

1. Car Enthusiasts: They have a deep interest in cars and are actively seeking for new cars in the market. Most of the time they are searching to a specific model or brand and are looking for the best possible deal. They may also be interested in rare or vintage cars and are looking for a platform that can help them find the car of their dreams.
2. Bargain Hunters: Majority of our users are likely to be on a budget and are looking for a good deal on a car. They may be interested in buying a used car or a car that is slightly older. They are looking for a platform that can help them find the best possible deal on a car.
3. First-time Car Buyers: These users are likely to be new to the car-buying process and may be unsure of what to look for in a car. They are looking for a platform that can help them find the right car for their needs and budget.

# Prerequisites

-   _Node and npm is the primary requirement_. Run the following command to check if node and npm is available in your system:

```
node -v
npm -v
```

`NOTE:` node version should be >14.0 because I am using `replaceAll()` which was not available in node version 14 or lower. If you want to still use node version <=14.0, you can use `split().join()` function instead.

-   _Git cli:_ Download Git command line interface using this [link](https://git-scm.com/downloads). If you are not sure if you have installed git on you machine, run the following command:

```
git -v
```

# How to use

1. Clone the tutorial repo using the below command.

```
git clone https://github.com/shivam-patel-123/bid-my-ride.git
```

2. Go inside the created folder and install dependencies

```
cd bid-my-ride/client
npm install

cd bid-my-ride/server
npm install
```

3. Create `.env` file at the root level of `server` directory and create some environment variables. This file should look like this:

```
MONGO_URI = <PASTE URI OF MONGODB>
SECRET_KEY = <JWT_SECRET>
```

4. Run the application using below command

```
cd client
npm start
```

Above commands will run React app and below command will run our BidMyRide server.

```
cd ../server
npm run dev
```

# Features:

## **Car Listings Management**

-   **Send a Sell car request to admin:** This task is the core of the entire application. Everything revolves around car lisiting. For example, with car listing, admin can do various tasks such as approving and rejecting car listing request and Starting a new Auction.
-   **Approve/Reject Car Listing request:** It is also one on the important tasks to maintain the reliability of the platform. Admin only has the rights to Approve and Reject Sell car request.
-   **Update Car Listing Details:** User only has the rights to edit the details of car. Even admin can't edit the details of user's car listing requests. It is important to note that listing with the status in `Under Review` is editable.
-   **Delete A Car Listing:** Listings Under Review is only deletable.
-   **Add Car as Favorite:** The platform is expected to have a lot of car listings. Thus, providing a feature to add car as a favorite is an improtant assets.
-   **Filter Car Listings by My listings and Favorites:** This task is related to the above tasks (Add Car as Favorite). It will only show a list of cars that are being added as a favorite by a user.

## **Car Documents Management**

-   **Upload Car Documents:** Users can upload multiple documents of their car in pdf format for admin to review. It will give admin the proof of reliability and existence of a car.
-   **Download Car Documents:** Uses can download their uploaded documents of a car. It is worth to note that admin can download documents of any car listing (Obviously).

## **User Profile Management**

-   **User registration:** User registration is the process of creating an account or profile on a website or platform, which allows a user to access certain features and content that may not be available to non-registered users. Typically, the registration process involves providing personal information such as name, email address, password.
-   **User login:** User login is the process of accessing a BIDMYRIDE using a set of credentials that have previously been created during the user registration process. Typically, users enter their email address and password to authenticate their identity and gain access to their account.
-   **View user profile:** Viewing a user profile is the process of accessing a page of a BIDMYRIDE that displays information about a specific user. User profiles can provide a variety of information such as their name and email.
-   **Update user profile:** A user profile update page is a web page within a BIDMYRIDE that allows users to edit and update their profile information. This page displays the user's current profile information, such as their name, email and password(optional), and provides a form or interface for users to make changes to this information.

-   **Forgot password:** A forgot password page is a web page within a BIDMYRIDE website that allows users who have forgotten their password to reset it. This page prompts the user to enter their email address , and then they can set the new password for their account.The purpose of a forgot password page is to provide users with a convenient and secure way to regain access to their account if they have forgotten their password.
-   **User logout:** User logout is the process of ending a user's current session on a BIDMYRIDE website, which involves terminating their access to the website and logging them out of their account. When a user logs out, they are redirected to a login page.The purpose of user logout is to protect the user's account and personal information by ensuring that unauthorized individuals cannot access their account or make changes to their profile.
-   **Delete user account:** Deleting an account refers to the process of permanently removing a user's account and all associated data from a BIDMYRIDE websitem. This process involves the user initiating the deletion process and confirming their intention to delete their account, after which the platform will permanently remove all data associated with the account.

# Backend Folder Structure

```
server
├── public
│   ├── assets
│   │   └── documents
│   │   └── images
├── src
│   ├── app.js
│   ├── config.js
│   ├── constants
│   ├── controllers
│   ├── models
│   ├── routes
│   └── utils
└── .env
```

We have followed MVC architecture. It consists of three main folders: `controllers, models and routes`. We decided to put the static files outside of the main server code in order to isolated the business logic away from public files like images and car documents. `constants` directory consists of all the string constants used in the server code. It is really important when the application scales and new featues are added into the existing project. When we talk about scaling, `config.js` also plays an important role. It contains all the configuration of the node application like the url of the backend server, etc.

# Sources Used

## **Images**

All images used in the project is taken from [Unsplash](https://www.unsplash.com). Images from this stock images are free to use for personal as well as professional use, no attribution required.

## **Icons**

Icons are taken from [Google Material Icons](https://fonts.google.com/icons). All icons are free to use for personal an projessional use with no attribution required.

## **Code Snippet Referred**

### `server/src/controllers/documentController.js`

_Lines 56 - 60_

```
const archive = archiver("zip", {
    zlib: { level: 9 },
});

archive.glob("**/*", { cwd: dirPath });
```

The code above was created by adapting the code in [NPM registry](https://www.npmjs.com/package/archiver) as shown below:

```
const output = fs.createWriteStream(__dirname + '/example.zip');
const archive = archiver('zip', {
  zlib: { level: 9 } // Sets the compression level.
});

archive.glob('file*.txt', {cwd:__dirname});
```

-   Code was implemented by [ctalkington](https://www.npmjs.com/~ctalkington).
-   I have modified the code to read all the files from a folder rather than using the particular file to make zip of. You can compare this in `archive.glob()` function. Also, I have used this in a different context.
