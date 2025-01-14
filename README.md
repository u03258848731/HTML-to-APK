<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Champion Trophy 2025 Live TV</title>
    <style>
        /* Basic Reset */
        body, html {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            height: 100%;
            background-color: #000;
            color: #fff;
        }

        /* Fullscreen Container */
        .fullscreen-container {
            position: relative;
            width: 100%;
            height: 100%;
            background-color: #000;
        }

        /* Banner Ad */
        .banner-ad {
            width: 100%;
            height: 50px;
            background-color: #333;
            text-align: center;
            line-height: 50px;
            color: white;
            font-size: 14px;
        }

        /* Reward Popup */
        .reward-popup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 20px;
            border-radius: 10px;
            display: none;
            z-index: 1000;
        }

        /* Match Player Fullscreen */
        .fullscreen-match {
            width: 100%;
            height: 100%;
            background: black;
            display: none;
        }

        /* Loading Spinner */
        .spinner {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            border: 4px solid #f3f3f3;
            border-top: 4px solid #3498db;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 2s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>

    <!-- Unity Ads SDK -->
    <script type="text/javascript" src="https://ssl.gstatic.com/doubleclick/novelty/adsdk/unityads.js"></script>
</head>
<body>

    <!-- Fullscreen Match Player -->
    <div class="fullscreen-container" id="match-container">
        <div class="spinner" id="loading-spinner"></div>
        <div class="fullscreen-match" id="match-player">
            <iframe src="https://crichd.com.co/crichd13012025" frameborder="0" width="100%" height="100%" onload="matchLoaded()"></iframe>
        </div>
    </div>

    <!-- Banner Ad -->
    <div class="banner-ad" id="unity-banner">
        <p>Banner Ad Here (Unity Ads will show here)</p>
    </div>

    <!-- Reward Ad Popup -->
    <div class="reward-popup" id="reward-popup">
        <p>Watch an ad to earn rewards!</p>
        <button onclick="closeRewardPopup()">Close</button>
    </div>

    <script>
        // Unity Ads Initialization
        const unityAdId = "5774285"; // Your Unity Ad ID
        let isRewardedAdReady = false;

        // Initialize Unity Ads
        function initializeUnityAds() {
            unityads.initialize(unityAdId, function(status) {
                if (status === "READY") {
                    console.log("Unity Ads Initialized Successfully!");
                } else {
                    console.log("Unity Ads Failed to Initialize.");
                }
            });
        }

        // Show Rewarded Ad
        function showRewardAd() {
            if (isRewardedAdReady) {
                unityads.showRewardedVideo("rewardedVideo", function(adResult) {
                    if (adResult === "COMPLETED") {
                        alert("You earned rewards for watching the ad!");
                    } else {
                        alert("You skipped the ad.");
                    }
                });
            } else {
                alert("Rewarded ad not ready!");
            }
        }

        // Show Banner Ad
        function showBannerAd() {
            unityads.showBanner("banner", {position: "top"});
        }

        // Callback when rewarded ad is ready
        unityads.on("rewardedVideoAdReady", function() {
            isRewardedAdReady = true;
            console.log("Rewarded Video Ad is ready!");
        });

        // Match loaded function
        function matchLoaded() {
            document.getElementById('loading-spinner').style.display = 'none';
            document.getElementById('match-player').style.display = 'block';
        }

        // Open match in fullscreen mode
        function openMatchFullScreen() {
            const matchPlayer = document.getElementById('match-player');
            matchPlayer.style.display = 'block'; // Show fullscreen match
        }

        // Show Reward Ad Popup
        function showRewardPopup() {
            const rewardPopup = document.getElementById('reward-popup');
            rewardPopup.style.display = 'block';
        }

        // Close Reward Ad Popup
        function closeRewardPopup() {
            const rewardPopup = document.getElementById('reward-popup');
            rewardPopup.style.display = 'none';
            showRewardAd(); // Trigger the reward ad when popup is closed
        }

        // Trigger Reward Popup after 3 seconds (adjust as needed)
        setTimeout(() => {
            showRewardPopup();
        }, 3000);

        // Initialize Unity Ads when the page is loaded
        window.onload = function() {
            initializeUnityAds();
            showBannerAd();
            openMatchFullScreen();
        };
    </script>

</body>
</html>
